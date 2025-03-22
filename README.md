# Micro vs Macro tasks in JavaScript

## Event Loop

The event loop is basic a endless loop that process tasks from a queue on a “first come – first served” basis.

The basic operating mode of the engine is to execute the tasks then sleeps, waiting for more tasks.

The tasks in a queue are called "macrotask queue".

Two important points:

1. The DOM is only rendered after the task is completed;
2. If a tasks take to long, due to complex calculations or a programming error (like a infinite loop), after some time it raises an alert like “Page Unresponsive”, to kill the task with the whole page.

### Macro and Micro tasks

Macrotasks can be scheduled from our code as well as other sources (ex: setTimeout, setInterval, scripts, etc.).

Microtasks come only from our code (ex: Promises, await, queueMicroTask, process.nextTick, etc.).

**Immediately after every macrotask, the engine executes all tasks from microtask queue, prior to running any other macrotasks or rendering or anything else.**

## Example

```js
console.log(1);

setTimeout(() => console.log(2));

Promise.resolve().then(() => console.log(3));

Promise.resolve().then(() => setTimeout(() => console.log(4)));

Promise.resolve().then(() => console.log(5));

setTimeout(() => console.log(6));

console.log(7);
```

The output should be: 1 7 3 5 2 6 4. (Full explanation [here](https://javascript.info/event-loop#what-will-be-the-output-of-this-code))

## References

- [Event loop: microtasks and macrotasks](https://javascript.info/event-loop)
- [Difference between microtask and macrotask within an event loop context](https://stackoverflow.com/questions/25915634/difference-between-microtask-and-macrotask-within-an-event-loop-context)
- [MicroTask and MacroTask in Javascript](https://www.naukri.com/code360/library/microtask-and-macrotask-in-javascript)

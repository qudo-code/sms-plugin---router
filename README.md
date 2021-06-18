[⬅ Back](/)
# Plugin Router
Map states to URLs. 

#### URL Params
URL params will be stored in your state machine `context` under the `router.params` property.
[⬅ Back to 🍕](https://github.com/qudo-lucas/state-machine-ui)
# Components Plugin 🔌
```javascript

// Example router options.
// router({
//     "/#/home" : "stateA",
// }),

// URL: "/#/home?id=xxx-xx

// state machine config
states : {
    stateA : {
        entry : ({ router }) => console.log("URL PARAM ID", router.params.id) // xxx-xx
    }
}

```

#### Example
```javascript
import stateUI, { plugins } from "state-ui";
import { createMachine, interpret } from "xstate";

// XState things
const config = { /* ...your machine config */ };
const machine = createMachine(config);
const service = interpret(machine);

// Pull off desired plugin(s)
const {
    logger,
    components,
    router
} = plugins;

// Apply desired stateUI plugins and settings.
stateUI({
    config,
    service,
    plugins : [
        router({
            "/#/home" : "main.home",
            "/#/about" : "main.about",
        }),
    ]
});

// Start service after
service.start();
```# sms-plugin---router

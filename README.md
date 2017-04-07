# api documentation for  [worker-farm (v1.3.1)](https://github.com/rvagg/node-worker-farm)  [![npm package](https://img.shields.io/npm/v/npmdoc-worker-farm.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-worker-farm) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-worker-farm.svg)](https://travis-ci.org/npmdoc/node-npmdoc-worker-farm)
#### Distribute processing tasks to child processes with an über-simple API and baked-in durability & custom concurrency options.

[![NPM](https://nodei.co/npm/worker-farm.png?downloads=true)](https://www.npmjs.com/package/worker-farm)

[![apidoc](https://npmdoc.github.io/node-npmdoc-worker-farm/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-worker-farm_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-worker-farm/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-worker-farm/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-worker-farm/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "authors": [
        "Rod Vagg @rvagg <rod@vagg.org> (https://github.com/rvagg)"
    ],
    "bugs": {
        "url": "https://github.com/rvagg/node-worker-farm/issues"
    },
    "dependencies": {
        "errno": ">=0.1.1 <0.2.0-0",
        "xtend": ">=4.0.0 <4.1.0-0"
    },
    "description": "Distribute processing tasks to child processes with an über-simple API and baked-in durability & custom concurrency options.",
    "devDependencies": {
        "tape": ">=3.0.3 <3.1.0-0"
    },
    "directories": {},
    "dist": {
        "shasum": "4333112bb49b17aa050b87895ca6b2cacf40e5ff",
        "tarball": "https://registry.npmjs.org/worker-farm/-/worker-farm-1.3.1.tgz"
    },
    "gitHead": "36edd5f28b05bd08b99c3543ab2be87e53e11dbf",
    "homepage": "https://github.com/rvagg/node-worker-farm",
    "keywords": [
        "worker",
        "child",
        "processing",
        "farm"
    ],
    "license": "MIT",
    "main": "./lib/index.js",
    "maintainers": [
        {
            "name": "rvagg",
            "email": "rod@vagg.org"
        },
        {
            "name": "amasad",
            "email": "amjad.masad@gmail.com"
        }
    ],
    "name": "worker-farm",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/rvagg/node-worker-farm.git"
    },
    "scripts": {
        "test": "node ./tests/"
    },
    "version": "1.3.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module worker-farm](#apidoc.module.worker-farm)
1.  [function <span class="apidocSignatureSpan">worker-farm.</span>end (api, callback)](#apidoc.element.worker-farm.end)
1.  [function <span class="apidocSignatureSpan">worker-farm.</span>farm (options, path)](#apidoc.element.worker-farm.farm)
1.  object <span class="apidocSignatureSpan">worker-farm.</span>farm.prototype

#### [module worker-farm.farm](#apidoc.module.worker-farm.farm)
1.  [function <span class="apidocSignatureSpan">worker-farm.</span>farm (options, path)](#apidoc.element.worker-farm.farm.farm)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.</span>TimeoutError (message, cause)](#apidoc.element.worker-farm.farm.TimeoutError)

#### [module worker-farm.farm.prototype](#apidoc.module.worker-farm.farm.prototype)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>addCall (call)](#apidoc.element.worker-farm.farm.prototype.addCall)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>childKeys ()](#apidoc.element.worker-farm.farm.prototype.childKeys)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>childTimeout (childId)](#apidoc.element.worker-farm.farm.prototype.childTimeout)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>end (callback)](#apidoc.element.worker-farm.farm.prototype.end)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>mkhandle (method)](#apidoc.element.worker-farm.farm.prototype.mkhandle)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>onExit (childId)](#apidoc.element.worker-farm.farm.prototype.onExit)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>processQueue ()](#apidoc.element.worker-farm.farm.prototype.processQueue)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>receive (data)](#apidoc.element.worker-farm.farm.prototype.receive)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>send (childId, call)](#apidoc.element.worker-farm.farm.prototype.send)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>setup (methods)](#apidoc.element.worker-farm.farm.prototype.setup)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>startChild ()](#apidoc.element.worker-farm.farm.prototype.startChild)
1.  [function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>stopChild (childId)](#apidoc.element.worker-farm.farm.prototype.stopChild)



# <a name="apidoc.module.worker-farm"></a>[module worker-farm](#apidoc.module.worker-farm)

#### <a name="apidoc.element.worker-farm.end"></a>[function <span class="apidocSignatureSpan">worker-farm.</span>end (api, callback)](#apidoc.element.worker-farm.end)
- description and source-code
```javascript
function end(api, callback) {
  for (var i = 0; i < farms.length; i++)
    if (farms[i] && farms[i].api === api)
      return farms[i].farm.end(callback)
  process.nextTick(callback.bind(null, 'Worker farm not found!'))
}
```
- example usage
```shell
...
  , workers    = workerFarm(require.resolve('./child'))
  , ret        = 0

for (var i = 0; i < 10; i++) {
  workers('#' + i + ' FOO', function (err, outp) {
    console.log(outp)
    if (++ret == 10)
      workerFarm.end(workers)
  })
}
'''

We'll get an output something like the following:

'''
...
```

#### <a name="apidoc.element.worker-farm.farm"></a>[function <span class="apidocSignatureSpan">worker-farm.</span>farm (options, path)](#apidoc.element.worker-farm.farm)
- description and source-code
```javascript
function Farm(options, path) {
  this.options     = extend(DEFAULT_OPTIONS, options)
  this.path        = path
  this.activeCalls = 0
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.worker-farm.farm"></a>[module worker-farm.farm](#apidoc.module.worker-farm.farm)

#### <a name="apidoc.element.worker-farm.farm.farm"></a>[function <span class="apidocSignatureSpan">worker-farm.</span>farm (options, path)](#apidoc.element.worker-farm.farm.farm)
- description and source-code
```javascript
function Farm(options, path) {
  this.options     = extend(DEFAULT_OPTIONS, options)
  this.path        = path
  this.activeCalls = 0
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.worker-farm.farm.TimeoutError"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.</span>TimeoutError (message, cause)](#apidoc.element.worker-farm.farm.TimeoutError)
- description and source-code
```javascript
TimeoutError = function (message, cause) {
  init.call(this, type, message, cause)
  //TODO: the specificity here is stupid, errno should be available everywhere
  if (type == 'FilesystemError') {
    this.code    = this.cause.code
    this.path    = this.cause.path
    this.errno   = this.cause.errno
    this.message =
      (errno.errno[this.cause.errno]
        ? errno.errno[this.cause.errno].description
        : this.cause.message)
      + (this.cause.path ? ' [' + this.cause.path + ']' : '')
  }
  Error.call(this)
  if (Error.captureStackTrace)
    Error.captureStackTrace(this, arguments.callee)
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.worker-farm.farm.prototype"></a>[module worker-farm.farm.prototype](#apidoc.module.worker-farm.farm.prototype)

#### <a name="apidoc.element.worker-farm.farm.prototype.addCall"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>addCall (call)](#apidoc.element.worker-farm.farm.prototype.addCall)
- description and source-code
```javascript
addCall = function (call) {
  if (this.ending)
    return this.end() // don't add anything new to the queue
  this.callQueue.push(call)
  this.processQueue()
}
```
- example usage
```shell
...
    var args = Array.prototype.slice.call(arguments)
    if (this.activeCalls >= this.options.maxConcurrentCalls) {
      var err = new MaxConcurrentCallsError('Too many concurrent calls (' + this.activeCalls + ')')
      if (typeof args[args.length - 1] == 'function')
        return process.nextTick(args[args.length - 1].bind(null, err))
      throw err
    }
    this.addCall({
        method   : method
      , callback : args.pop()
      , args     : args
      , retries  : 0
    })
  }.bind(this)
}
...
```

#### <a name="apidoc.element.worker-farm.farm.prototype.childKeys"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>childKeys ()](#apidoc.element.worker-farm.farm.prototype.childKeys)
- description and source-code
```javascript
childKeys = function () {
  var cka = Object.keys(this.children)
    , cks

  if (this.searchStart >= cka.length - 1)
    this.searchStart = 0
  else
    this.searchStart++

  cks = cka.splice(0, this.searchStart)

  return cka.concat(cks)
}
```
- example usage
```shell
...

  if (!this.callQueue.length)
    return this.ending && this.end()

  if (this.activeChildren < this.options.maxConcurrentWorkers)
    this.startChild()

  for (cka = this.childKeys(); i < cka.length; i++) {
    childId = +cka[i]
    if (this.children[childId].activeCalls < this.options.maxConcurrentCallsPerWorker
  && this.children[childId].calls.length < this.options.maxCallsPerWorker) {

this.send(childId, this.callQueue.shift())
if (!this.callQueue.length)
  return this.ending && this.end()
...
```

#### <a name="apidoc.element.worker-farm.farm.prototype.childTimeout"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>childTimeout (childId)](#apidoc.element.worker-farm.farm.prototype.childTimeout)
- description and source-code
```javascript
childTimeout = function (childId) {
  var child = this.children[childId]
    , i

  if (!child)
    return

  for (i in child.calls) {
    this.receive({
        idx   : i
      , child : childId
      , args  : [ new TimeoutError('worker call timed out!') ]
    })
  }
  this.stopChild(childId)
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.worker-farm.farm.prototype.end"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>end (callback)](#apidoc.element.worker-farm.farm.prototype.end)
- description and source-code
```javascript
end = function (callback) {
  var complete = true
  if (this.ending === false)
    return
  if (callback)
    this.ending = callback
  else if (this.ending == null)
    this.ending = true
  Object.keys(this.children).forEach(function (child) {
    if (!this.children[child])
      return
    if (!this.children[child].activeCalls)
      this.stopChild(child)
    else
      complete = false
  }.bind(this))

  if (complete && typeof this.ending == 'function') {
    process.nextTick(function () {
      this.ending()
      this.ending = false
    }.bind(this))
  }
}
```
- example usage
```shell
...
  , workers    = workerFarm(require.resolve('./child'))
  , ret        = 0

for (var i = 0; i < 10; i++) {
  workers('#' + i + ' FOO', function (err, outp) {
    console.log(outp)
    if (++ret == 10)
      workerFarm.end(workers)
  })
}
'''

We'll get an output something like the following:

'''
...
```

#### <a name="apidoc.element.worker-farm.farm.prototype.mkhandle"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>mkhandle (method)](#apidoc.element.worker-farm.farm.prototype.mkhandle)
- description and source-code
```javascript
mkhandle = function (method) {
  return function () {
    var args = Array.prototype.slice.call(arguments)
    if (this.activeCalls >= this.options.maxConcurrentCalls) {
      var err = new MaxConcurrentCallsError('Too many concurrent calls (' + this.activeCalls + ')')
      if (typeof args[args.length - 1] == 'function')
        return process.nextTick(args[args.length - 1].bind(null, err))
      throw err
    }
    this.addCall({
        method   : method
      , callback : args.pop()
      , args     : args
      , retries  : 0
    })
  }.bind(this)
}
```
- example usage
```shell
...
}.bind(this)
}

// a constructor of sorts
Farm.prototype.setup = function (methods) {
var iface
if (!methods) { // single-function export
  iface = this.mkhandle()
} else { // multiple functions on the export
  iface = {}
  methods.forEach(function (m) {
    iface[m] = this.mkhandle(m)
  }.bind(this))
}
...
```

#### <a name="apidoc.element.worker-farm.farm.prototype.onExit"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>onExit (childId)](#apidoc.element.worker-farm.farm.prototype.onExit)
- description and source-code
```javascript
onExit = function (childId) {
  // delay this to give any sends a chance to finish
  setTimeout(function () {
    var doQueue = false
    if (this.children[childId] && this.children[childId].activeCalls) {
      this.children[childId].calls.forEach(function (call, i) {
        if (!call) return
        else if (call.retries >= this.options.maxRetries) {
          this.receive({
              idx   : i
            , child : childId
            , args  : [ new ProcessTerminatedError('cancel after ' + call.retries + ' retries!') ]
          })
        } else {
          call.retries++
          this.callQueue.unshift(call)
          doQueue = true
        }
      }.bind(this))
    }
    this.stopChild(childId)
    doQueue && this.processQueue()
  }.bind(this), 10)
}
```
- example usage
```shell
...
        , activeCalls : 0
        , exitCode    : null
      }

  forked.child.on('message', this.receive.bind(this))
  forked.child.once('exit', function (code) {
    c.exitCode = code
    this.onExit(id)
  }.bind(this))

  this.activeChildren++
  this.children[id] = c
}

// stop a worker, identified by id
...
```

#### <a name="apidoc.element.worker-farm.farm.prototype.processQueue"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>processQueue ()](#apidoc.element.worker-farm.farm.prototype.processQueue)
- description and source-code
```javascript
processQueue = function () {
  var cka, i = 0, childId

  if (!this.callQueue.length)
    return this.ending && this.end()

  if (this.activeChildren < this.options.maxConcurrentWorkers)
    this.startChild()

  for (cka = this.childKeys(); i < cka.length; i++) {
    childId = +cka[i]
    if (this.children[childId].activeCalls < this.options.maxConcurrentCallsPerWorker
        && this.children[childId].calls.length < this.options.maxCallsPerWorker) {

      this.send(childId, this.callQueue.shift())
      if (!this.callQueue.length)
        return this.ending && this.end()
    }<span class="apidocCodeCommentSpan"> /*else {
      console.log(
        , this.children[childId].activeCalls < this.options.maxConcurrentCallsPerWorker
        , this.children[childId].calls.length < this.options.maxCallsPerWorker
        , this.children[childId].calls.length , this.options.maxCallsPerWorker)
    }*/
</span>  }

  if (this.ending)
    this.end()
}
```
- example usage
```shell
...
        call.retries++
        this.callQueue.unshift(call)
        doQueue = true
      }
    }.bind(this))
  }
  this.stopChild(childId)
  doQueue && this.processQueue()
}.bind(this), 10)
}

// start a new worker
Farm.prototype.startChild = function () {
this.childId++
...
```

#### <a name="apidoc.element.worker-farm.farm.prototype.receive"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>receive (data)](#apidoc.element.worker-farm.farm.prototype.receive)
- description and source-code
```javascript
receive = function (data) {
  var idx     = data.idx
    , childId = data.child
    , args    = data.args
    , child   = this.children[childId]
    , call

  if (!child) {
    return console.error(
        'Worker Farm: Received message for unknown child. '
      + 'This is likely as a result of premature child death, '
      + 'the operation will have been re-queued.'
    )
  }

  call = child.calls[idx]
  if (!call) {
    return console.error(
        'Worker Farm: Received message for unknown index for existing child. '
      + 'This should not happen!'
    )
  }

  if (this.options.maxCallTime !== Infinity)
    clearTimeout(call.timer)

  if (args[0] && args[0].$error == '$error') {
    var e = args[0]
    switch (e.type) {
      case 'TypeError': args[0] = new TypeError(e.message); break
      case 'RangeError': args[0] = new RangeError(e.message); break
      case 'EvalError': args[0] = new EvalError(e.message); break
      case 'ReferenceError': args[0] = new ReferenceError(e.message); break
      case 'SyntaxError': args[0] = new SyntaxError(e.message); break
      case 'URIError': args[0] = new URIError(e.message); break
      default: args[0] = new Error(e.message)
    }
    args[0].type = e.type
    args[0].stack = e.stack

    // Copy any custom properties to pass it on.
    Object.keys(e).forEach(function(key) {
      args[0][key] = e[key];
    });
  }

  process.nextTick(function () {
    call.callback.apply(null, args)
  })

  ;delete child.calls[idx]
  child.activeCalls--
  this.activeCalls--

  if (child.calls.length >= this.options.maxCallsPerWorker
      && !Object.keys(child.calls).length) {
    // this child has finished its run, kill it
    this.stopChild(childId)
  }

  // allow any outstanding calls to be processed
  this.processQueue()
}
```
- example usage
```shell
...
// delay this to give any sends a chance to finish
setTimeout(function () {
  var doQueue = false
  if (this.children[childId] && this.children[childId].activeCalls) {
    this.children[childId].calls.forEach(function (call, i) {
      if (!call) return
      else if (call.retries >= this.options.maxRetries) {
        this.receive({
            idx   : i
          , child : childId
          , args  : [ new ProcessTerminatedError('cancel after ' + call.retries + ' retries!') ]
        })
      } else {
        call.retries++
        this.callQueue.unshift(call)
...
```

#### <a name="apidoc.element.worker-farm.farm.prototype.send"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>send (childId, call)](#apidoc.element.worker-farm.farm.prototype.send)
- description and source-code
```javascript
send = function (childId, call) {
  var child = this.children[childId]
    , idx   = child.calls.length

  child.calls.push(call)
  child.activeCalls++
  this.activeCalls++

  child.send({
      idx    : idx
    , child  : childId
    , method : call.method
    , args   : call.args
  })

  if (this.options.maxCallTime !== Infinity) {
    call.timer =
      setTimeout(this.childTimeout.bind(this, childId), this.options.maxCallTime)
  }
}
```
- example usage
```shell
...
this.children[id] = c
}

// stop a worker, identified by id
Farm.prototype.stopChild = function (childId) {
var child = this.children[childId]
if (child) {
  child.send('die')
  setTimeout(function () {
    if (child.exitCode === null)
      child.child.kill('SIGKILL')
  }, this.options.forcedKillTime)
  ;delete this.children[childId]
  this.activeChildren--
}
...
```

#### <a name="apidoc.element.worker-farm.farm.prototype.setup"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>setup (methods)](#apidoc.element.worker-farm.farm.prototype.setup)
- description and source-code
```javascript
setup = function (methods) {
  var iface
  if (!methods) { // single-function export
    iface = this.mkhandle()
  } else { // multiple functions on the export
    iface = {}
    methods.forEach(function (m) {
      iface[m] = this.mkhandle(m)
    }.bind(this))
  }

  this.searchStart    = -1
  this.childId        = -1
  this.children       = {}
  this.activeChildren = 0
  this.callQueue      = []

  if (this.options.autoStart) {
    while (this.activeChildren < this.options.maxConcurrentWorkers)
      this.startChild()
  }

  return iface
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.worker-farm.farm.prototype.startChild"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>startChild ()](#apidoc.element.worker-farm.farm.prototype.startChild)
- description and source-code
```javascript
startChild = function () {
  this.childId++

  var forked = fork(this.path)
    , id     = this.childId
    , c      = {
          send        : forked.send
        , child       : forked.child
        , calls       : []
        , activeCalls : 0
        , exitCode    : null
      }

  forked.child.on('message', this.receive.bind(this))
  forked.child.once('exit', function (code) {
    c.exitCode = code
    this.onExit(id)
  }.bind(this))

  this.activeChildren++
  this.children[id] = c
}
```
- example usage
```shell
...
  this.childId        = -1
  this.children       = {}
  this.activeChildren = 0
  this.callQueue      = []

  if (this.options.autoStart) {
    while (this.activeChildren < this.options.maxConcurrentWorkers)
      this.startChild()
  }

  return iface
}

// when a child exits, check if there are any outstanding jobs and requeue them
Farm.prototype.onExit = function (childId) {
...
```

#### <a name="apidoc.element.worker-farm.farm.prototype.stopChild"></a>[function <span class="apidocSignatureSpan">worker-farm.farm.prototype.</span>stopChild (childId)](#apidoc.element.worker-farm.farm.prototype.stopChild)
- description and source-code
```javascript
stopChild = function (childId) {
  var child = this.children[childId]
  if (child) {
    child.send('die')
    setTimeout(function () {
      if (child.exitCode === null)
        child.child.kill('SIGKILL')
    }, this.options.forcedKillTime)
    ;delete this.children[childId]
    this.activeChildren--
  }
}
```
- example usage
```shell
...
      } else {
        call.retries++
        this.callQueue.unshift(call)
        doQueue = true
      }
    }.bind(this))
  }
  this.stopChild(childId)
  doQueue && this.processQueue()
}.bind(this), 10)
}

// start a new worker
Farm.prototype.startChild = function () {
this.childId++
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

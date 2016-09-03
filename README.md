

# log
`import "github.com/tmc/log"`

* [Overview](#pkg-overview)
* [Index](#pkg-index)

## <a name="pkg-overview">Overview</a>
Package log wraps logrus to include source line/function information




## <a name="pkg-index">Index</a>
* [func Debug(args ...interface{})](#Debug)
* [func Debugln(args ...interface{})](#Debugln)
* [func Error(args ...interface{})](#Error)
* [func Errorln(args ...interface{})](#Errorln)
* [func Fatal(args ...interface{})](#Fatal)
* [func Fatalln(args ...interface{})](#Fatalln)
* [func Info(args ...interface{})](#Info)
* [func Infoln(args ...interface{})](#Infoln)
* [func SetLevel(level Level)](#SetLevel)
* [func Warn(args ...interface{})](#Warn)
* [func Warnln(args ...interface{})](#Warnln)
* [type Level](#Level)
* [type Logger](#Logger)
  * [func Base() Logger](#Base)
  * [func New() Logger](#New)
  * [func With(key string, value interface{}) Logger](#With)
  * [func WithError(err error) Logger](#WithError)


#### <a name="pkg-files">Package files</a>
[doc.go](/src/github.com/tmc/log/doc.go) [log.go](/src/github.com/tmc/log/log.go) 





## <a name="Debug">func</a> [Debug](/src/target/log.go?s=4534:4565#L167)
``` go
func Debug(args ...interface{})
```
Debug logs a message at level Debug on the standard logger.



## <a name="Debugln">func</a> [Debugln](/src/target/log.go?s=4673:4706#L172)
``` go
func Debugln(args ...interface{})
```
Debugln logs a message at level Debug on the standard logger.



## <a name="Error">func</a> [Error](/src/target/log.go?s=5358:5389#L197)
``` go
func Error(args ...interface{})
```
Error logs a message at level Error on the standard logger.



## <a name="Errorln">func</a> [Errorln](/src/target/log.go?s=5497:5530#L202)
``` go
func Errorln(args ...interface{})
```
Errorln logs a message at level Error on the standard logger.



## <a name="Fatal">func</a> [Fatal](/src/target/log.go?s=5638:5669#L207)
``` go
func Fatal(args ...interface{})
```
Fatal logs a message at level Fatal on the standard logger.



## <a name="Fatalln">func</a> [Fatalln](/src/target/log.go?s=5777:5810#L212)
``` go
func Fatalln(args ...interface{})
```
Fatalln logs a message at level Fatal on the standard logger.



## <a name="Info">func</a> [Info](/src/target/log.go?s=4812:4842#L177)
``` go
func Info(args ...interface{})
```
Info logs a message at level Info on the standard logger.



## <a name="Infoln">func</a> [Infoln](/src/target/log.go?s=4947:4979#L182)
``` go
func Infoln(args ...interface{})
```
Infoln logs a message at level Info on the standard logger.



## <a name="SetLevel">func</a> [SetLevel](/src/target/log.go?s=4076:4102#L152)
``` go
func SetLevel(level Level)
```
SetLevel sets the Level of the base logger



## <a name="Warn">func</a> [Warn](/src/target/log.go?s=5084:5114#L187)
``` go
func Warn(args ...interface{})
```
Warn logs a message at level Warn on the standard logger.



## <a name="Warnln">func</a> [Warnln](/src/target/log.go?s=5219:5251#L192)
``` go
func Warnln(args ...interface{})
```
Warnln logs a message at level Warn on the standard logger.




## <a name="Level">type</a> [Level](/src/target/log.go?s=133:149#L3)
``` go
type Level uint8
```
Level describes the log severity level


``` go
const (
    // PanicLevel level, highest level of severity. Logs and then calls panic with the
    // message passed to Debug, Info, ...
    PanicLevel Level = iota
    // FatalLevel level. Logs and then calls `os.Exit(1)`. It will exit even if the
    // logging level is set to Panic.
    FatalLevel
    // ErrorLevel level. Logs. Used for errors that should definitely be noted.
    // Commonly used for hooks to send errors to an error tracking service.
    ErrorLevel
    // WarnLevel level. Non-critical entries that deserve eyes.
    WarnLevel
    // InfoLevel level. General operational entries about what's going on inside the
    // application.
    InfoLevel
    // DebugLevel level. Usually only enabled when debugging. Very verbose logging.
    DebugLevel
)
```









## <a name="Logger">type</a> [Logger](/src/target/log.go?s=1032:1418#L27)
``` go
type Logger interface {
    SetLevel(level Level)
    SetOut(out io.Writer)

    Debug(...interface{})
    Debugln(...interface{})

    Info(...interface{})
    Infoln(...interface{})

    Warn(...interface{})
    Warnln(...interface{})

    Error(...interface{})
    Errorln(...interface{})

    Fatal(...interface{})
    Fatalln(...interface{})

    With(key string, value interface{}) Logger
    WithError(err error) Logger
}
```
Logger is an interface that describes logging







### <a name="Base">func</a> [Base](/src/target/log.go?s=3987:4005#L147)
``` go
func Base() Logger
```
Base returns the base logger.


### <a name="New">func</a> [New](/src/target/log.go?s=3880:3897#L142)
``` go
func New() Logger
```
New returns a new logger


### <a name="With">func</a> [With](/src/target/log.go?s=4201:4248#L157)
``` go
func With(key string, value interface{}) Logger
```
With attaches a key,value pair to a logger.


### <a name="WithError">func</a> [WithError](/src/target/log.go?s=4374:4406#L162)
``` go
func WithError(err error) Logger
```
WithError returns a Logger that will print an error along with the next message.



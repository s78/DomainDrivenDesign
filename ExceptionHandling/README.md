# Exception Handling

### Simple Guidelines
* Check arguments in public methods and throw ArgumentException or ArgumentNullException.
* Use try-catch for external calls.
* Do not create and throw an Exception instance. (Throw an ApplicationException if not a custom exception.)
* Do not catch a NullReferenceException. (This is a programing error. Check for null explicitly instead.)
* Use separate catch statements for each exception. (Do not type-check an exception.)

### General Guidelines

* Use try-catch for operations that might not work all the time. (See "When to Use try-catch" below for details.)"
* Try not to "catch all". (It is OK to start doing so and then refine later when there are no side effects and the process can be repeated.)
``` csharp
try
{
    ...
}
catch (Exception ex)
{
    ....
}
```

* Wrap a domain-specific exception with a custom exception
``` csharp
try
{
    ...
}
catch (SqlException ex)
{
    // do not bubble up this domain-specific exception if this can be a cross-layer or cross-assembly call...
    throw new NameNotFoundException("The specified name does not exist.", ex);
}
```

* Log exceptions that need to be monitored and/or fixed.
* Set up a top-level error handler (even only for logging purposes).

> Craching an application due to an unhandled exception may sometimes be a better solution than keeping it running in a corrupted state.

### When to Use try-catch
* IO operations (database calls, file systems, web requests, etc.)







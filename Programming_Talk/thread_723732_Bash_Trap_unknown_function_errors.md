---
title: "Bash: Trap unknown function errors"
date: 2008-03-13
forum: Programming Talk
---

### Post by irkengir on 2008-03-13
Does anybody know if it is possible to trap an unknown function error and handle it?

Ideally what I would like to do is map all undefined function errors to a handler and have it prepend a string to the function name and then perform the call if a function by that new name exists.

```

# <code that set up handle as the handler for an unknown command>
handle () {
    # $tried contains the function that we tried to call and handled
    set | if grep "$tried ()"; then
        "handled_$tried" "$@"
        return $?
    fi
    echo "neither $tried or handled_$tried exist"
}

handled_foo () {
    echo "this is $FUNCNAME: $@"
}
foo hello # should output "this is handled_foo: hello "

```

I've looked through all the trap signals and even ran this:```
#!/usr/bin/env bash
handle () {
    echo handled!
}
trap handle SIGHUP SIGINT SIGQUIT SIGILL SIGTRAP SIGABRT SIGEMT SIGFPE SIGKILL SIGBUS SIGSEGV SIGSYS SIGPIPE SIGALRM SIGTERM SIGUSR1 SIGUSR2 SIGCHLD SIGWINCH SIGURG SIGSTOP SIGTSTP SIGCONT SIGTTIN SIGTTOU SIGVTALRM SIGPROF SIGXCPU SIGXFSZ
nonexist
``` to no avail.

Can trap DEBUG help at all?

---

### Post by ghostdog74 on 2008-03-13
try [ this]("http://tldp.org/LDP/abs/html/debugging.html") first

---

### Post by irkengir on 2008-03-14
OK I read it. But I'm not debugging.

---

### Post by mssever on 2008-03-14
I don't think that what you're trying to do is possible in Bash. AFAIK, signals come from other processes, but functions live in the same process as the shell executing the code. Bash simply doesn't have good enough error-handling capabilities.

This would be trivial in Ruby, however. ```
#!/usr/bin/env ruby

#wrapping this in a class isn't necessary, but I prefer doing so to prevent ambiguity
class Demo
  def handle_foo
    #do stuff
  end
  
  # This is where the magic happens
  def method_missing(method_name, *args)
    test = "handle_#{method_name}".to_sym
    if respond_to? test
      send test, *args
    else
      raise NoMethodError
    end
  end
end

a = Demo.new
a.foo
```

---

### Post by irkengir on 2008-03-14
> don't think that what you're trying to do is possible in Bash.Yeah I suspected that.

Yeah I know this is possible in Ruby, it is also in PHP.

Thanks anyway.

---


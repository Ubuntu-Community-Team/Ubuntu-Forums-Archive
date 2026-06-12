---
title: "Perl - how do I save the output of a system call into a variable without file I/O"
date: 2007-08-15
forum: Programming Talk
---

### Post by jimmymus on 2007-08-15
I know how to use system() and pipe it into a file, then open that file and pull out what I just piped in. There has got to be a function in perl where I can do a system call and the return value of the function is the output of the system call.

Anyone help me out? Thanks

---

### Post by shawnhcorey on 2007-08-15
> **jimmymus said:**
> I know how to use system() and pipe it into a file, then open that file and pull out what I just piped in. There has got to be a function in perl where I can do a system call and the return value of the function is the output of the system call.

Anyone help me out? Thanks

Two ways:

The backtick method:
```
my $var = `command arguments`;
```

The pipe method:
```
open my $fh, 'command arguments |' or die "cannot run command: $!";
{
  local $/;
  $var = <$fh>;
}
close $fh;
```

---

### Post by LionsFate on 2007-08-15
> **jimmymus said:**
> I know how to use system() and pipe it into a file, then open that file and pull out what I just piped in. There has got to be a function in perl where I can do a system call and the return value of the function is the output of the system call.

Anyone help me out? Thanks

man IPC::Open2

or -

man IPC::Open3

---

### Post by slavik on 2007-08-15
> **shawnhcorey said:**
> Two ways:

The backtick method:
```
my $var = `command arguments`;
```

The pipe method:
```
open my $fh, 'command arguments |' or die "cannot run command: $!";
{
  local $/;
  $var = <$fh>;
}
close $fh;
```
with the pipe version, don't leave that space between last character of the command and the pipe symbol, it has never worked (for me).

---


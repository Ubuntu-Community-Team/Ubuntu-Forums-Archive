---
title: "Execute a program from code written in VALA"
date: 2009-07-26
forum: Programming Talk
---

### Post by arkashkin on 2009-07-26
Hello, I'm trying to execute some shell commands from program I'm writing in VALA language. In C language I could use the - execv command, but how to do that in VALA? And just one more question, can i write VALA code mixed with C code ?

---

### Post by qwerty12 on 2009-07-27
Disclaimer: I suck at Vala, and I'm still learning to code, but since you haven't recieved any replies, I figure I may as well post what I know (in hope of a better reply as it'd benefit me too).

execl can be used like this:
```

using Posix;

static void main ()
{
        execl("/bin/sh", "/bin/sh", "-c", "ls", null);
} 

```

But Vala uses GLib so why not use one of its spawning functions? ([http://references.valadoc.org/glib-2.0/GLib.Process.spawn_async.html](http://references.valadoc.org/glib-2.0/GLib.Process.spawn_async.html))

```

void on_async_exit (Pid pid, int status)
{
        Process.close_pid(pid);
}

static void main() {
        string[] runme = { "/bin/ls", null };
        Pid pid;
        if (!Process.spawn_async (null, runme, null, SpawnFlags.DO_NOT_REAP_CHILD, null, out pid)) return;
        ChildWatch.add (pid, on_async_exit);
}

```

As I say, someone may have a better answer, but this can't hurt...

---

### Post by arkashkin on 2009-07-28
This is how I finally did it:

```
public static void execProgram()
{
         string[] argv = new string[1];
	        argv[0] = "/home/arkashkin/tt"; //tt is the name of the program
	        //argv[1] = null;
	       
	        Pid child_pid;
	        int input_fd;
	        int output_fd;
	        int error_fd;
	        try {
	        Process.spawn_async_with_pipes(
	            command_line,
	            argv, //argv
	            null,   // environment
	            SpawnFlags.SEARCH_PATH,
	            null,   // child_setup
	            out child_pid,
	            out input_fd,
	            out output_fd,
	            out error_fd);
	       }
	       catch (Error e) {
         stderr.printf ("Could not load UI: %s\n", e.message);
         }	            
}


```

Thanks for those who replayed.

---

### Post by rpuchadm on 2010-03-10
using Posix;

static void main ()
{
        execl("/bin/ls", "-lha");
}

compiled with

valac exec.vala -o exec --pkg posix

and executes by

./exec

just works...... i think simpler


SORRY the program does not continue, execl replaces the process

---

### Post by arkashkin on 2010-03-10
thanks.

---


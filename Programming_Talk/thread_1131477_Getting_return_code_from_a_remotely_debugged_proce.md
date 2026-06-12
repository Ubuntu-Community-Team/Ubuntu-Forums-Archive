---
title: "Getting return code from a remotely debugged process"
date: 2009-04-20
forum: Programming Talk
---

### Post by ranthal on 2009-04-20
Hi all,

I am going through some software tests for an embedded platform in which I need to force the failure of a user space application executed during a startup script.  The application itself performs a number of crypto tests, one of which I specifically need to break in order to cause a system halt.  The sw test is being done using gdb to remotely debug the application, so we have made a modified version of the startup to launch the application using gdbserver.

So here's the problem: the startup script is supposed to grab the return code of the application and from this decide if the crypto tests passed or failed.  When I launch it using gdbserver the return code I grab is from gdbserver so even though I correctly broke the test I receive a return code of 0 and everything keeps moving as if nothing ever happened.

Any suggestions on how to get my script to use the correct return code?

GDB has a -return-child-result option but this is only useful from the remote debug location and not actually on the target itself.

This is not a part of the normal startup I just need to do it in order to prove a couple specific test cases so the structure of my startup should remain the same and I still need to use the startup script.

Thanks

---

### Post by Arndt on 2009-04-21
> **ranthal said:**
> Hi all,

I am going through some software tests for an embedded platform in which I need to force the failure of a user space application executed during a startup script.  The application itself performs a number of crypto tests, one of which I specifically need to break in order to cause a system halt.  The sw test is being done using gdb to remotely debug the application, so we have made a modified version of the startup to launch the application using gdbserver.

So here's the problem: the startup script is supposed to grab the return code of the application and from this decide if the crypto tests passed or failed.  When I launch it using gdbserver the return code I grab is from gdbserver so even though I correctly broke the test I receive a return code of 0 and everything keeps moving as if nothing ever happened.

Any suggestions on how to get my script to use the correct return code?

GDB has a -return-child-result option but this is only useful from the remote debug location and not actually on the target itself.

This is not a part of the normal startup I just need to do it in order to prove a couple specific test cases so the structure of my startup should remain the same and I still need to use the startup script.

Thanks

The gdbserver program does this (and a lot of other things, of course):

	```
  if (status == 'W')
	    fprintf (stderr,
		     "\nChild exited with status %d\n", signal);


		  fprintf (stderr, "GDBserver exiting\n");
		  exit (0);

```

So it prints the exit status but throws it away. It seems straighforward to change it to do "exit(signal)" instead. gdbserver is a part of gdb.

---


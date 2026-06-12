---
title: "Sending Control C to a process in java."
date: 2008-11-28
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2008-11-28
Hey All

I'm writing a java app that uses arecord and allows the user to terminate it when they need to.  The problem is that I don't know how to send the Control-C signal to it.  I started it like this:

```

	String com1 = "/bin/bash -c arecord -f cd -t raw | lame -x - ";
	String com2 = date;
	String com3 = ".mp3";
	String fullCom = com1 + com2 + com3;
	

	try {

		Process record = Runtime.getRuntime().exec(fullCom);
		
		// then stop the recording
		System.out.println("Recording.  Enter any key to stop recording.");

// etc, etc

```

It runs well, but I can't find a way to stop it cleanly so that it actually saves the file...  when I use record.destroy() or exit(0), the file is not saved.  Does anyone know how to send the Control-C signal to this process?
Thanks a lot!

---

### Post by slavik on 2008-11-28
kill -2 pid

I think control-C is sigint ...

---

### Post by the_real_fourthdimension on 2008-11-28
That's just what I needed.  Thanks a lot!

EDIT:  Very interesting... when I run this program, I can see the correct processes running in top and they all have pids, but no file results.  When I run the same commands that are being run through the program in the terminal, an output file is produced.  Through some print statements I've found that the commands I want and the commands that are actually being called are the same, so there's no error there...  I'm kind of stumped.  If the same commands are being run, why does one work and one not?  Does anyone know what's going on? Thanks.

P.S.  I circumvented the problem by having the program create a bash script for this command, but I'm still very curious why it wouldn't work the other way.

---


---
title: "Java inperprocess communication"
date: 2008-06-28
forum: Programming Talk
---

### Post by Phristen on 2008-06-28
I'm using Runtine.getRuntime().exec(command); to launch another process, and I wanna communicate with it via the input and output streams.
When the process is something like "ls", it is very simple - just keep reading from process.getInputStream() until the end of file...

However, when the new process communicates back, I start running in trouble...
So, basically, I need some tutorials that deal with this issue (i.e. two-way communication), and I haven't been able to find anything useful so far :(
Any links?

P.S. As an example, I'm using the crafty chess engine. It accepts input in plain text and outputs also in plain text... However, my input (I use a PrintWriter obtained from processes' getOutputStream()) doesn't seem to be getting to the destination :(

---

### Post by xlinuks on 2008-06-28
Well I'm too lazy to try out and do what you're doing to find out what's the matter.. as a side note, since you didn't post the source code I can only guess, perhaps you are using multiple println() and since (prolly) the target app reads till the first \n character it might eventually stop reading after the first call of println and since the info is crippled it shows no sign of having gotten any command from you.
Do a test and see what you actually _print_ to that app, and then send that stuff manually (from the console) and see whether that app now works, draw conclusions from the results.

---

### Post by geirha on 2008-06-28
Yes, do as xlinuks suggests. The cat command is perfect for such testing. If you run cat with no arguments, it will simply output to stdout each line you input to stdin, untill eof. Flushing the output-stream might help as well.

---

### Post by Phristen on 2008-06-28
> Well I'm too lazy to try out and do what you're doing to find out what's the matter.. I know, that's why I merely need a working example, from which I can build my own.

I get a feeling I'm missing something really silly and obvious, though it isn't the miltiple printlns.

P.S. I'm gonna go try it with cat, good idea.

---

### Post by Phristen on 2008-06-28
Ok, here's what I have:[PHP]
		try {proc = Runtime.getRuntime().exec("cat");} catch (IOException e) {}
		in = new BufferedReader(new InputStreamReader(proc.getInputStream()));
		out = new PrintWriter(new OutputStreamWriter(proc.getOutputStream()));
		try {
			
			out.write("hello");
			
			System.out.println(">> ");
			String s = in.readLine();
			System.out.println(">> " + s);
		} catch (Exception e) {e.printStackTrace();}

[/PHP]The output of above is ">>".
In other works, it just hangs (doesn't crash) at in.readLine() :(
I tried separating the reading and writing in separate threads but to the same effect.

P.S. ooookay, wait a sec, I just flushed the output stream and it seems to work... I'll do some more testing.
P.S. Yep, it works :)
Basically, the solution was to use println instead of write (or add "\n" to the string), and flush the stream right away.
Makes me feel so smart hehe.

---


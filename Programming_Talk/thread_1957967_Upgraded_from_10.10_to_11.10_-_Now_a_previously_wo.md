---
title: "Upgraded from 10.10 to 11.10 - Now a previously working project no longer compiles"
date: 2012-04-13
forum: Programming Talk
---

### Post by shumifan50 on 2012-04-13
Upgraded from Ubuntu 10.10 to 11.10 (through 11.04).
This installed new Eclipse Indigo (upgraded from galileo).

Downloaded Mysql source, built, installed and tested - works fine.
Downloaded Mysql CPP connector source, compiled and installed.

Fired up Eclipse and compiled - initially got some errors where the compiler had been tightened up (bad programmer LOL).

The I get 'undefined reference to get_driver_instance' on all programs that use mysql. 

Double checked:
libmysqlcppconn.so references libmysqlcppconn.so.5.1.1 and is in both /usr/local/lib and /usr/lib and that path is set in Eclipse.

Copied the compile string from the Eclipse console window and pasted it in a terminal and compiled - same problem.
Jiggled the visible libraries around to see if the sequence was bad - same problem.

Ran "nm" against the lib...so and lib,,,.a and both contain, what seems a like a reasonble, entry to get_driver_instance.

Now I am at my wits end - it looks like the library is being ignored.
Here is the string I ran from the terminal:

g++ -L/usr/local/lib /Debug" -o"CImageFrame"  ./CImageFrame.o   -lmysqlcppconn -lMagick++ 

Where can I see what the default search paths are? I looked at the output from env and nothing there seems to reference link directories.


Any help in resolving this will be greatly appreciated as it has now stopped the project dead in its tracks.

---

### Post by dwhitney67 on 2012-04-13
You indicated that you were using Eclipse, then you pasted the command that you used within a terminal.

Did Eclipse not work, and the terminal did, or did both attempts fail?

From the looks of the command you use in the terminal, I'm surprised that you did not have to specify -lmysql as one of the libraries, even though technically for get_instance_driver() all you need is -lmysqlcppconn.

Anyhow, if you could clarify exactly what command Eclipse is using, that might be helpful.  And if you made a mistake with the command that you entered in the terminal, please re-post the corrected command.

Edit:
> 
Where can I see what the default search paths are?

I almost forgot; try this:
```

g++ --print-search-dirs

```

P.S.  Did you ever consider using MySQL++ in lieu of Connector C++?

---

### Post by t1497f35 on 2012-04-13
11.10 did the [toolchain transition]("https://wiki.ubuntu.com/NattyNarwhal/ToolchainTransition") and people reporting about undefined stuff while compiling are usually those unaware of this transition and hence affected by this. Make sure you're doing only **direct linking** and other stuff as specified above.

---

### Post by shumifan50 on 2012-04-13
@t1497f35:

That was it, I was caught be the sequence of library linking. The compile line I showed is a VERy simplified version of what was being compiled and under the new rules there were sequencing errors in the libraries. Once I sorted these out the project compiles both from Eclipse and the command line.

Thanks for that link.

I might mention that 'nm' is also valuable in establishing what is required.

@dwhitney67:
Thanks for the pointers and how to get the paths.
> I'm surprised that you did not have to specify -lmysql as one of the libraries,
It only required libmysqlcppconn.so, not libmysql.so to work. Might be a further problem later LOL.

---


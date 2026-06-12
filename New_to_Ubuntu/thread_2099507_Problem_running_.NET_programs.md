---
title: "Problem running .NET programs"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by Kbkb on 2012-12-29
Hello, i have ubuntu 12.10 and i want to run a .NET framework program, so i downloaded mono, But i got the following error:
> kbkb@Abood:~$ mono '/home/kbkb/PoyonBETA52REL2/PoyonBETA.exe' 
Unknown heap type: CLR


Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for A.ca0bd7bef7494e82623b6769762b80fb8 ---> System.ArgumentException: Encoding name 'Shift-JIS' not supported
Parameter name: name
  at System.Text.Encoding.GetEncoding (System.String name) [0x00000] in <filename unknown>:0 
  at A.ca4e3692ac990e316430778ea750e013d.c43806262bede0edb02eb7d808c51f91f (System.String ) [0x00000] in <filename unknown>:0 
  at A.ca0bd7bef7494e82623b6769762b80fb8..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeInitializationException: An exception was thrown by the type initializer for A.ca0bd7bef7494e82623b6769762b80fb8 ---> System.ArgumentException: Encoding name 'Shift-JIS' not supported
Parameter name: name
  at System.Text.Encoding.GetEncoding (System.String name) [0x00000] in <filename unknown>:0 
  at A.ca4e3692ac990e316430778ea750e013d.c43806262bede0edb02eb7d808c51f91f (System.String ) [0x00000] in <filename unknown>:0 
  at A.ca0bd7bef7494e82623b6769762b80fb8..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---

 Thanks for help.

---

### Post by gnush on 2012-12-29
Running .NET on an operating system other than Windows is ugly. Hell, even running it on Windows is ugly. May I ask why you want to do this? 

I'm not really good at deciphering stacks and exceptions, but did it close down instantly after you ran the program?

After a quick google search I wound up with this: **[http://forum.winehq.org/viewtopic.php?t=14674](http://forum.winehq.org/viewtopic.php?t=14674)** Maybe you'll find some information on there. There also seems to be some encoding problems - have you installed Shift JIS?

Sorry if my post wasn't helpful, I don't know much about wine or mono, I'm just brainstorming here.

---

### Post by Kbkb on 2012-12-29
> **gnush said:**
> Running .NET on an operating system other than Windows is ugly. Hell, even running it on Windows is ugly. May I ask why you want to do this? 

I'm not really good at deciphering stacks and exceptions, but did it close down instantly after you ran the program?

After a quick google search I wound up with this: **[http://forum.winehq.org/viewtopic.php?t=14674](http://forum.winehq.org/viewtopic.php?t=14674)** Maybe you'll find some information on there. There also seems to be some encoding problems - have you installed Shift JIS?

Sorry if my post wasn't helpful, I don't know much about wine or mono, I'm just brainstorming here.
Thank you i installed .NET framework using winetricks and it works like a charm. thank you again :)

---


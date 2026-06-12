---
title: "Flash player in desktop application"
date: 2012-02-06
forum: Programming Talk
---

### Post by eric318 on 2012-02-06
Hi,

I am trying to work out an approach to developing a desktop application that would play movies, games and various flash material such as flash games and flash flip books. The movies will be in both video format and swf format, and will need to be  compressed and encrypted for transmission to users and decompressed/decrypted by our player so as not be viewable by other players.

The installer would be platform / OS dependant. The player / user interface would need to be written in a 'portable' language so it can be cross-complied to different platforms  ( Windows, Linux/Android, Mac, Iphone/Ipad, ... )

The idea here is to ideally maintain one code base so the client will experience the same interface on each platform we support.

 
My questions are-

What would be the best approach to develop these applications?

Is it possible to acquire public / open source code where much of the work has already been done and then

add my code to it?

If open source code is available where could I get it from

Thanks

---

### Post by epicoder on 2012-02-06
As for embedding flash in your application, a good place to start might be the source code for Mozilla Firefox, which you can get [here]("https://developer.mozilla.org/en/Download_Mozilla_Source_Code"). However, if you use their code:
[QUOTE=http://www.mozilla.org/MPL/2.0/FAQ.html]I want to distribute (outside my organization) an executable program based on MPL-licensed source code that I have modified. What do I have to do?

You must make available the MPL-licensed portions of the source code as   described in the [next paragraph], and inform the recipients how they can   obtain such source code (Section 3.2).

I want to distribute (outside my organization) MPL-licensed source code that I have modified. What do I have to do?

To see the complete set of requirements, read the license. However, generally:


[LIST]
[*]     You must inform the recipients that the source code is made available to them under the terms of the MPL (Section 3.1), including any Modifications (as defined in Section 1.10) that you have created.
[*]     You must make the grants described in Section 2 of the license.
[*]     You must respect the restrictions on removing or altering notices in the source code (Section 3.4).
[/LIST]
 [/QUOTE]
Note that if you include Flash content in your application, you probably will not be able to port to the iDevice family as they don't support Flash. You will still be able to port to Mac, though.

---

### Post by Lampang on 2012-02-08
If it's all Flash stuff, can't you use Air? Or is that being abandoned by Adobe?

---


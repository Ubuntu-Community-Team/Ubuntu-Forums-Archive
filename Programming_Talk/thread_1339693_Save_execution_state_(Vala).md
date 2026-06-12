---
title: "Save execution state (Vala)"
date: 2009-11-27
forum: Programming Talk
---

### Post by kumoshk on 2009-11-27
Are there any libraries for saving the execution state of my entire program and reloading it later? I know there are things I can use to save parts of it (and technically, I could do some work to get it all), but I'm curious if they have anything to make it all happen in one go.

---

### Post by nvteighen on 2009-11-28
> **kumoshk said:**
> Are there any libraries for saving the execution state of my entire program and reloading it later? I know there are things I can use to save parts of it (and technically, I could do some work to get it all), but I'm curious if they have anything to make it all happen in one go.

Wow... you want a Lisp image :p

Serioulsy, I haven't seen this functionality in any other language than Lisp, which has it because of historical reasons.

Vala comes from the C-world, so the need of such an idea is actually strange: It's a statically compiled language, so your image is your compiled executable.

What you could do is to serialize all your objects and functions into some file, but it sounds almost like writing a new compiler for a dynamic dialect of Vala...

---

### Post by kumoshk on 2009-11-28
Curious.

Hmm. I'm basically just wondering how so many programs, such as document viewers, etc. can reload the exact state as before with seemingly no processing time, while any approach I've seen in code, so far, takes a noticeable amount of time to load large documents into the widget. I figured they have to be saving the state or something. I mean, just loading a file so large can take more time than it takes them to re-open one at the right spot (like re-opening is faster than normal opening).

So do you think they just do regular serialization? Would that give this effect?

Thanks for the note on Lisp. Sounds worth looking into some day.

---

### Post by nvteighen on 2009-11-28
> **kumoshk said:**
> Curious.

Hmm. I'm basically just wondering how so many programs, such as document viewers, etc. can reload the exact state as before with seemingly no processing time, while any approach I've seen in code, so far, takes a noticeable amount of time to load large documents into the widget. I figured they have to be saving the state or something. I mean, just loading a file so large can take more time than it takes them to re-open one at the right spot (like re-opening is faster than normal opening).

So do you think they just do regular serialization? Would that give this effect?

Er... You mean like evince when it shows you the PDF exactly where you were looking at? That can be easily done using some cache associationg filename and position... or even other things like what toolbar and preferences were activated. That whole thing can be done with a regular text file you parse.

What I understood from your post was that you wanted to save the program's current state in RAM and dump it into disk but in a way you could restore it exactly as it was and resume execution. That's a very different thing: it means to save the whole thing, which is useful in dynamic contexts for example when you're trying out something in the interpreter and want to save your session; and it's also useful for deploying Lisp programs. What you want, instead, is to save the state with respect to some specific file or situation which can be easily restored from the program's functionality.

---

### Post by kumoshk on 2009-11-28
So, what's the difference between loading the saved stuff from a text file and loading the original text file (given it is a text file), as far as speed goes? How do you account for the difference? FBreader with plain txt files is an example of what I mean; I'm not sure if there's a speed difference with Evince, though.  (There was no icon saying the program was still running in memory, with FBreader.)

---

### Post by nvteighen on 2009-11-28
> **kumoshk said:**
> So, what's the difference between loading the saved stuff from a text file and loading the original text file (given it is a text file), as far as speed goes? How do you account for the difference? FBreader with plain txt files is an example of what I mean; I'm not sure if there's a speed difference with Evince, though.  (There was no icon saying the program was still running in memory, with FBreader.)

Hm... well, I think you can't do the second thing with a text file; it's just plain text and there's no way to store "display state" inside the text file so that the file itself can tell the program what the state was.

That's why I suggest you a cache system. The program should create a text file with the needed information to recreate the display state. The cache should be a configuration directory in which all those text files would be stored. For convenience, the cache file's filename should somehow conect it with the original file (whatever format it is), so that it is also opened when the desired file is and the display state gets restored.

---


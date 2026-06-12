---
title: "[SOLVED] C++: Sockets, multithreading and http"
date: 2008-04-12
forum: Programming Talk
---

### Post by Lau_of_DK on 2008-04-12
Hey,


Im a recent MS/VS/C#&C++ convert and Im struggling a bit in finding the right libaries, IDEs and tutorials for Linux.

1. I need to build a network application, that among other things can open a network connection for a server and communication asynchronously. When I read through /sys/socket.h I do not see any implementation of asynchronous functions. In C# I would use something like BeginAccept(Socket, Callback proc, params), how do you guys set up async. communication in your c++ apps?

2. This app will need to download files from http/ftp servers.Does any of you have a quick-references guide to interface with HTTP servers?

Thanks alot,
Lau

Ps. Is there an IDE for Linux that is a little bit like Visual Studio? Just the same ball-park would be fine.

---

### Post by LaRoza on 2008-04-12
> **Lau_of_DK said:**
> Hey,

Im a recent MS/VS/C#&C++ convert and Im struggling a bit in finding the right libaries, IDEs and tutorials for Linux.

1. I need to build a network application, that among other things can open a network connection for a server and communication asynchronously. When I read through /sys/socket.h I do not see any implementation of asynchronous functions. In C# I would use something like BeginAccept(Socket, Callback proc, params), how do you guys set up async. communication in your c++ apps?

Ps. Is there an IDE for Linux that is a little bit like Visual Studio? Just the same ball-park would be fine.

The sticky has the IDE question answered, and specifically mentions VS. (This is a FAQ)

Here is the page on my wiki, with a link to socket programming. It may help: [http://laroza.pbwiki.com/SpecificL](http://laroza.pbwiki.com/SpecificL)

You can use C# in Linux if you want also.

---

### Post by Lau_of_DK on 2008-04-12
> **LaRoza said:**
> The sticky has the IDE question answered, and specifically mentions VS. (This is a FAQ)

Here is the page on my wiki, with a link to socket programming. It may help: [http://laroza.pbwiki.com/SpecificL](http://laroza.pbwiki.com/SpecificL)

You can use C# in Linux if you want also.

Thank you for your reply. I forgot to mention that I had already read the sticky and tried out the suggested IDEs.

Regarding multithreaded socket-applications: I have already read the link on your page and it does not provide any help in regards to building this type of application.  (if it does, its beyond my comprehension anyway).

/Lau

---

### Post by LaRoza on 2008-04-12
You said you used C#; can you not use it now?

---

### Post by tseliot on 2008-04-13
I think you can do that with C++ and QT4. Have a look at [this page]("http://doc.trolltech.com/4.3/qtnetwork.html#details"). And of course QT4 is cross platform.

As regards IDEs, you can try[ Eclipse with the QT4 plugin]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download") (with the designer, etc.) or Kdevelop.

---

### Post by Lau_of_DK on 2008-04-13
> **LaRoza said:**
> You said you used C#; can you not use it now?

I dont know. It would really blow my mind if they have produced a C# compiler that works like the one on Windows - Its a huge system, I imagine a port would have taken 15 years to do, but maybe I should try it out. Now that I was on Linux I was hoping to switch back to C++ as it has a more low-level feel to it. 

[QUOTE=tseliot]
I think you can do that with C++ and QT4. Have a look at this page. And of course QT4 is cross platform.

As regards IDEs, you can try Eclipse with the QT4 plugin (with the designer, etc.) or Kdevelop.
[/QUOTE]

I'll give a whirl, thanks for the recommendation. Regarding the page with Networking classes, its quite a read, so I'll get back to you once I've paved my way through it, but thank you very much so far, its looks like the stuff I need.

/Lau

---

### Post by LaRoza on 2008-04-13
> **Lau_of_DK said:**
> I dont know. It would really blow my mind if they have produced a C# compiler that works like the one on Windows - Its a huge system, I imagine a port would have taken 15 years to do, but maybe I should try it out. Now that I was on Linux I was hoping to switch back to C++ as it has a more low-level feel to it. 

I'll give a whirl, thanks for the recommendation. Regarding the page with Networking classes, its quite a read, so I'll get back to you once I've paved my way through it, but thank you very much so far, its looks like the stuff I need.

/Lau

C# has been implemented in the Mono project. It implements the standards and many things that are not part of the ECMA standard.

Perhaps you could try it out.

(Mono works on Windows too)

---

### Post by kknd on 2008-04-13
I don't know if its of your interest, but I have wrote a C++ wrapper of sockets (lgpl), at [http://oproj.tuxfamily.org](http://oproj.tuxfamily.org). Works with MS-Windows too.

---

### Post by Lau_of_DK on 2008-04-15
> **kknd said:**
> I don't know if its of your interest, but I have wrote a C++ wrapper of sockets (lgpl), at [http://oproj.tuxfamily.org](http://oproj.tuxfamily.org). Works with MS-Windows too.

Thank you for that, its absolutely of interest. I've already started reading :)

To everybody who replied, thanks alot for your help, so many interesting things have been unpacked in this thread. If I knew how to close the thread I would, I'm already doing multhreaded networking now.

/Lau

---

### Post by tseliot on 2008-04-15
> **Lau_of_DK said:**
>  If I knew how to close the thread I would, I'm already doing multhreaded networking now.
All you have to do is select "Thread tools" and then "Mark this thread as solved". Next time you'll do it yourself.

---


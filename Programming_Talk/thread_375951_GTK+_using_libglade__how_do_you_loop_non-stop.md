---
title: "GTK+ using libglade : how do you loop non-stop?"
date: 2007-03-04
forum: Programming Talk
---

### Post by ZDemon on 2007-03-04
Hi guys,

I'm new to GTK+ programming in C. I use the autoconnect signals as well as using the Glade Interface Designer to write my app.

My question is, how do you insert instructions that loop together with gtk_main() ?

Example :

```
int main()
{
...
....
...
...
gtk_main();
My_Instructions();
return (0);
}

void My_instructions()
{
....
....
....
}


```

Now, button clicks and all that are signals. Only if you click them the instructions will run. What if i don't want to click on anything? I want the function My_Instruction to loop continuously without any key presses or button clicks. But of course the signals should still work.

The function My_Instructions() will only work if i quit gtk_main(). Well, of course. Duh.

Any solutions for this? There aren't much tutorials for this subject.

I'd appreciate any links for further studying too.

Thanks for any input.

---

### Post by lnostdal on 2007-03-04
here is an example of threading: [http://nostdal.org/~lars/programming/c/gtk-threads.c](http://nostdal.org/~lars/programming/c/gtk-threads.c) .. you should be able to figure this out

note that if more than one (more than your main thread) uses gdk/gtk you must use gdk_threads_enter and gdk_threads_leave to avoid problems

edit:
note that the "idle"-functions here might also be suitable for your task: [http://developer.gnome.org/doc/API/2.0/glib/glib-The-Main-Event-Loop.html](http://developer.gnome.org/doc/API/2.0/glib/glib-The-Main-Event-Loop.html)

..it is however important that these instructions (the function you pass to g_idle_add) you insert do not block out for long periods of time causing your gui to be non-responsive to events (you'll need threads, as used above, to be able to handle these cases)

---

### Post by ZDemon on 2007-03-04
Hi there lnostdal,

The example you gave was extremely helpful and taught me how to use threading. Its simple and effective. Extremely nice example.

Thanks a bunch. I don't think i can figure out stuff like this based on the GTK+ Reference docs by myself. They're too detailed, and i don't know where to look for info.

Thanks, threading was exactly what i needed.

Cheers :)

---

### Post by lnostdal on 2007-03-04
thank you for the feedback :)

the code did however contain some mistakes and over-simplifications which i have now corrected .. i also added some usage of widgets in the background thread to show you how gdk_threads_enter and gdk_threads_leave should be used .. make sure you check out the updated version(#1) :)

#1: when downloading using firefox it seems to sometimes cache the file causing the old version to be downloaded .... for now, if you use wget to download the file this does not happen

---

### Post by ZDemon on 2007-03-05
Hey thanks for the update.

So this is how you multitask within an application. I had the impression everything revolved around signals. 

Just a question, When i use threading and my loop never ends, does everything else becomes non-responsive? It doesn't seem so in the example.

Once again, nice updated example.

---

### Post by lnostdal on 2007-03-05
> **ZDemon said:**
> When i use threading and my loop never ends, does everything else becomes non-responsive?

no, this is exactly what threading solves .. it enables an application to do more than one thing at the "same time"

* one thread, the "main thread" here - handles events and keeps your GUI updated and responsive .. gtk_main() loops and continuously checks for pending events and handles them - it starts a loop that doesn't end until gtk_main_quit() is called .. that's why you in a one-thread situation can't do anything after gtk_main() is called(#1); it is said to be a "blocking call"

* while another thread handles tasks that might take a long time (or forever) to finish and when done in or from the main thread would lead to an unresponsive or sluggish GUI

i find threading quite interesting btw. :) .. a possible design here might be to take an object oriented approach where you have each task represented as an instance of a struct each containing members like should_run, already_running and a pointer to a function with the task to execute .. further with pointers to functions that represent taskStateReady and taskStateBusy in different contexts .. higher-order programming ftw.


#1: note the stuff i mentioned about g_idle_add though .. using that you might make the single main-thread handle parts of a big and time-consuming task once in a while .. you'll have to make sure none of the parts take up too much time though, or your GUI will become sluggish and unresponsive

---

### Post by ZDemon on 2007-03-05
Ahhh, so the CPU time is distributed. I understand it now.

I really appreciate your input. This kind of topic requires people with years of programming experience. I'm new to Linux. But i really like GTK programming.

Im doing some DSP related work for my university thesis. Ive already written the driver for my hardware. Now i need to design the GUI. I have to use the ALSA sound API. As you know, you have to keep polling to create sound. 

Thats why threading would really be useful to me.

Thanks for your help. Once Im done with my thesis Im gonna use what Ive learn to write some open source programs.

Cheers :)

---

### Post by lnostdal on 2007-03-05
yes, even if there is only one CPU (time slicing) what matters is the convenience for the programmer .. you can "pretend" that things will happen simultaneously or in parallel when you write your code

wikipedia works as an overview by the way: [http://en.wikipedia.org/wiki/Thread_%28computer_science%29](http://en.wikipedia.org/wiki/Thread_%28computer_science%29)

GTK is very nice yes .. i'm glad to be of some assistance :)

---


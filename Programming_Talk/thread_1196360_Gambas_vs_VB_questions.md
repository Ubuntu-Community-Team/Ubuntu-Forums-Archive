---
title: "Gambas vs VB questions"
date: 2009-06-24
forum: Programming Talk
---

### Post by nix-n00b on 2009-06-24
Hello, as you can tell from my nickname i am new to linux. I am a new college student for computer programming and one of my upcoming classes is learning Visual Basic. I heard Gambas is the closest thing for linux. I used a tutorial for a "Hello world" project just to start from ([http://www.vb6.us/tutorials/hello-world](http://www.vb6.us/tutorials/hello-world)) and it did not work, it kept giving me an error saying the END command something with the form. 

Then i tried this Gambas hello world tutorial i found online ([http://fosswire.com/post/2008/9/video-tutorial-simple-hello-world-application-in-gambas/](http://fosswire.com/post/2008/9/video-tutorial-simple-hello-world-application-in-gambas/)) and it worked great.

I guess my question is, are the command different? like it said for VB to type MsgBox "Hello world" and in Gambas was instructed to type Message.Info("Hello world!")

what is the difference between public and private sub and how do i get the program to close when they press the ok button? any help is appriciated, thanks in advance!

---

### Post by JordyD on 2009-06-24
Well, Gambas is not VB. It's a BASIC-*like* language. So yes, the functions, methods, commands, statements, etc. are bound to have many differences.

I'm not an expert on VB, but the Public/Private thing could be similar to C++'s Public and Private classes. I imagine that Google should be better able to answer that, though.

If you want to use VB, you can get MonoDevelop (in the repos). Unfortunately it doesn't yet support VB GUI designing, but you *can* code the GUI yourself. MonoDevelop will allow you to code and run VB, plus it has a nice development environment.

I've never used Gambas or VB in MonoDevelop before, although I can say that my first programming language was VB :), unfortunately on that I've mainly forgotten. Maybe I should start some coding with VB + MonoDevelop.

Last but not least, there is some friction over Mono (which MonoDevelop uses to compile VB, C#, etc.), but do some research before you blindly believe what the others may tell you. I personally see no problem with it, but others do. Anyways, good luck.

---

### Post by nix-n00b on 2009-06-24
Thanks for your reply, I just downloaded monodevelop from the repositorys. it seems to be harder to use then Gambas, since gambas has more of a visual code gui, instead of having to know the code you can design a program like when useing dreamweaver and such. Maybe i am wrong, is there a setting so it is all visual instead of notepad style codeing?

I think i get it, so Gambas is Linux version of MS's VB? so some of the string i would type in are going to be different some instead of print "Hello world" it maybe linuxprint "hello world", ect..? This is my first programming language besides HTML, and alooooong time ago turbo pascal and C, but forgot how to use them , im trying to relearn all this stuff. Thanks

edit:::

i found this link for Gambas which i thought may help other people who may have these same questions

[http://www1.cs.columbia.edu/~naliniv/presentations/2004-foss-gambas.pdf](http://www1.cs.columbia.edu/~naliniv/presentations/2004-foss-gambas.pdf)

---

### Post by JordyD on 2009-06-24
> **nix-n00b said:**
> Thanks for your reply, I just downloaded monodevelop from the repositorys. it seems to be harder to use then Gambas, since gambas has more of a visual code gui, instead of having to know the code you can design a program like when useing dreamweaver and such. Maybe i am wrong, is there a setting so it is all visual instead of notepad style codeing?

I think i get it, so Gambas is Linux version of MS's VB? so some of the string i would type in are going to be different some instead of print "Hello world" it maybe linuxprint "hello world", ect..? This is my first programming language besides HTML, and alooooong time ago turbo pascal and C, but forgot how to use them , im trying to relearn all this stuff. Thanks

I'm not sure what you mean... you can try **View > Toolbox**, if you want to be able to drag-n-drop statements.

I can't really say that much about Gambas since I've never used it, maybe someone else can give you a hand with that?

---

### Post by kalaharix on 2009-06-25
Hi

Have a look at [www.gambasdoc.org](www.gambasdoc.org) and search on Private and Public. It is all to do with whether the definition can be used outside the class.

Gambas is not 'VB for Linux'. It is a different beast and much easier to use (once you have experience of it, if that doesn't sound a stupid thing to say). Gambas shares many design concepts with Java and is extremely versatile. I am also finding that it is rock solid.

The documentation for Gambas is not really set up for newbies (believe me, I have found it hard work) but it is well worth the effort.

Closing the program:

Public Sub btnClose_click()
	me.close
end

You can also use FMain(or whatever).close

rgds

---


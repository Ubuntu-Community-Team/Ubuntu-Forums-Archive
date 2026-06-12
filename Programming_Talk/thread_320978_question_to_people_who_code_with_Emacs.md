---
title: "question to people who code with Emacs"
date: 2006-12-18
forum: Programming Talk
---

### Post by Houman on 2006-12-18
Hi there to all the Emacs fans;

I have been programming in small dozes on Linux for a while now, and all my friends who were really good used to use either Vi and Emacs, they all feared the modern editors like the plague.

I have been using Emacs since I thought they must know something I don't, but honestly as my projects get bigger and as the modern editors on Linux get better (Code::Blocks, KDevelop, Anjuta) its getting harder and harder to justify using such an ancient piece of technology. 

Now I am not trying to start another flame war, but Emacs lacks some serious features that i think any text editor should have. Like letting you navigate through your classes/files or some amount of code completion is very helpful. Now when I try to use some class defined elsewhere I have to find the file, open it in another frame, look at the method I want and the arguments. But with a decent programming IDE thats all done for you.

So could anyone please tell me how they can justify using Emacs when there are so many better editors out there? I am honestly asking this because I like emacs and having using it more than a year.

(also I know about ECB and similar extensions, they are pretty useless and make emacs very slow)

regards

Houman

---

### Post by reiatzu on 2006-12-18
I use vim personally. Emacs is a piece of @#$%. ;)

---

### Post by Wybiral on 2006-12-18
I write in gedit, compile with command line or makefiles... I too have tried emacs and simply don't see what all the hype is about... Maybe I missed something *shrug*

---

### Post by Houman on 2006-12-18
hi there,

Well most of the arguments I used against Emacs applies to those text editors too (gedit and vi). They lack the very useful features offered by better IDE's like class navigation and code completion and etc... 

So I am not starting an anti-emacs flamewar, just saying lets all drop this elitist mentality that a plain text editor will do the job and lets start using Code::blocks or what not, I mean technology has advanced! :)

I am not trying to be mean or anything, I know there is so much pressure from the gurus that if you dont use a plain old text editor youre a n00b, but Im gonna stop caring, I looked at Code::blocks and I think im ready to drop emacs in favour of it, although ill always use emacs on small files and scripts because its convenient (and when im ssh'ing).

Houman

---

### Post by lnostdal on 2006-12-18
> **Houman said:**
> Like letting you navigate through your classes/files or some amount of code completion is very helpful.

I type "m-v-b" and press tab: "multiple-value-bind" .. etc.

> **Houman said:**
>  Now when I try to use some class defined elsewhere I have to find the file, open it in another frame, look at the method I want and the arguments. 


Not needed; I press F1 and an internal browser shows me the API-docs for the stuff my cursor is hovering over. Also, if I have:

```

(defclass SomeType () ())
(defclass SomeOtherType () ())

(defmethod some-weird-method ((hard-to-remember-argumnet SomeType) (another-hard-to-remember-argument SomeOtherType))
  (write-line "Hello World!"))


```

then type "s-w-m" and press tab I get "some-weird-method"; and it shows information about arguments in the status-line at the bottom at the same time.

With a keypress I can jump to the definition of whatever my cursor is hovering over instantly.

When working with C I've bound some keys etc.. From my .emacs-file:

```

(add-hook 'c-mode-hook
          (function (lambda () 
                      (define-key c-mode-map [f5] 'compile)
                      (define-key c-mode-map [f6] 'next-error)
                      (define-key c-mode-map [f7] 'previous-error))))

(add-hook 'c++-mode-hook
          (function (lambda () 
                      (define-key c++-mode-map [f5] 'compile)
                      (define-key c++-mode-map [f6] 'next-error)
                      (define-key c++-mode-map [f7] 'previous-error))))

(setq compilation-ask-about-save nil)
(setq compilation-read-command nil)
(setq compilation-scroll-output t)
(setq compilation-window-height 10)
(setq compile-auto-highlight t)
(setq compile-command "scons -u")

```

 .. F5 recompiles all needed dependencies (using scons ofc.) .. F6 and F7 navigates files/buffers with regards to messages from the compiler; it's very fast and doesn't get in my way. 

..and most importantly; if something bothers me I'm able to fix or change it.

---

### Post by Houman on 2006-12-18
thank you lnostdal;

Thats a lot of useful info, and it will take me some time to go through all of it, I already added the last bit of shortcuts to my .emacs file. 

But I still think I have a point, in that its probably easier to use a modern editor than having to write how it should behave in Lisp. But lets see what other forum members think.

regards

Houman

---

### Post by raul_ on 2006-12-18
If u program with an IDE, you'lle learn how to program with that IDE, if u program with a text editor, u'll learn how to program

---

### Post by Keffin on 2006-12-18
For vim I point to the taglist plugin for class/file browsing  ([http://vim-taglist.sourceforge.net/images/taglist_c.gif](http://vim-taglist.sourceforge.net/images/taglist_c.gif)) and the fact that vim 7 has smart code completion for C, (X)HTML with CSS, JavaScript, PHP, Python, Ruby, SQL and XML. It also has a simpler word completion that looks through open files for any word that could be a completion for the current one, which works better than it might sound while coding.

I believe emacs has equivalents. Google certainly thinks so anyway.

For coding big things in Java at work I use eclipse, but aside from doing completion (much much) better it gets on my nerves at every turn. Hiding how things work really doesn't help when the program hiding things acts up; or doesn't have a nice GUI plugin for helper programs A, B, and C; or has a "nice GUI" that (I think) exposes all the options that axis provides, but with different names and confusing (lack of) descriptions - yes WTP, I'm looking at you :(.

I just know where I am much better when I don't have an IDE *trying* to work magic behind my back.

And just when I click preview I see this quote:
> If u program with an IDE, you'lle learn how to program with that IDE, if u program with a text editor, u'll learn how to program

Thank you raul_, I couldn't have said it better. You can see that because I tried and it took me this much text :D.

---

### Post by ohgod on 2006-12-18
> **raul_ said:**
> If u program with an IDE, you'lle learn how to program with that IDE, if u program with a text editor, u'll learn how to program

Nicely put.  I use Visual Studio 2005 at work, and while it's a truly excellent IDE, it hides a lot of stuff and makes it that much harder for me to write C# without it...

---

### Post by Houman on 2006-12-18
> 
It also has a simpler word completion that looks through open files for any word that could be a completion for the current one, which works better than it might sound while coding.

I believe emacs has equivalents. Google certainly thinks so anyway.


Did you read the part in my original post that i said:

> 
also I know about ECB and similar extensions, they are pretty useless and make emacs very slow


Also you guys are confusing what I am saying. 

> 
I just know where I am much better when I don't have an IDE trying to work magic behind my back.


There is nothing magical about a nice class navigation bar or code completion, you guys are thinking about something else. I hate it when an IDE generates code as much as the next guy. I will always write makefiles myself and will compile and run my projects from commandline and wont even want an IDE to do anything behind the scenes. But the features I mentioned are very different than when Visual Studio builds a skeleton of a project for you, its just assisting the coder in navigating through source code and giving him a hand when he is looking up a function prototype and similar utilities.

regards

Houman

---

### Post by Wybiral on 2006-12-18
I'm going to agree with raul_

I don't consider myself an elitist... I just prefer a simple editor of a clunky ide.
Gedit has tabs for multiple files, and syntax highlighting...
Thats about all you need. Just write a makefile...

If you run into trouble, the compiler will usually give you enough errors to bail you out.

---

### Post by raul_ on 2006-12-18
I like gVim's automatic indentation though :)

---

### Post by Houman on 2006-12-18
```

I don't consider myself an elitist... I just prefer a simple editor of a clunky ide.

```

sorry Wybiral, i didnt mean it to sound so harsh, should have rephrased that, my bad.

Well,  no one agrees with me so far, someone should write an email to developers of Anjuta/Code::blocks/Kdevelop and tell them to stop wasting their times, because Linux developers are just not interested [-(

regards

Houman

---

### Post by Wybiral on 2006-12-18
lol, I'm sure there's people who do use them. I just learned C++ and ASM in a simple text editor so it seems more natural that way. I tried code::blocks and anjuta but they were too distraction and bulky of an IDE for my taste (I even have to turn off the simple tool bar in gedit to be comfortable)

---

### Post by Keffin on 2006-12-18
> Did you read the part in my original post that i said:
Quote:
 also I know about ECB and similar extensions, they are pretty useless and make emacs very slow

Sorry, I actually both missed that and didn't know what ECB was. My experience is mostly with vim, and its taglist plugin has always worked very well and very quickly for me.

> There is nothing magical about a nice class navigation bar or code completion, you guys are thinking about something else. I hate it when an IDE generates code as much as the next guy.

Again I can only go off my experience and that is with eclipse and writing Java. You can't **just** tell eclipse to complete code for you, it starts generating all sorts of settings files and crap, and they tend to eventually sneak into version control and mess with other peoples settings.

Then I have to go to the command line to generate some new web service skeletons with axis because the eclipse front-end to it makes no sense, and a partner has modified axis to our needs anyway.

Then I want to do some complex refactoring that doesn't quite fit in with any of eclipses 50000 refactoring menu options (well aren't I awkward...) and I find myself in vim making a quick macro that will do the job faster than eclipse can load up.

Then after going through a whole custom outside-of-eclipse build/packaging process to conform to internal and external naming/documentation/whatever conventions - obviously eclipse hides the complexity to the point where there's just no point trying with it - I want to run tomcat, my program, postgreSQL, and eclipse at the same time. Oh dear... please wait 5 years while this operation completes...

If you don't find you also have these problems, and can JUST get code completion at no cost, then congratulations. Really, keep using that tool. But those are some reasons why eclipse (and every other IDE I've used) annoys me (and possibly other people).

> Well, no one agrees with me so far, someone should write an email to developers of Anjuta/Code::blocks/Kdevelop and tell them to stop wasting their times, because Linux developers are just not interested

You did address the post to emacs users :P.

---

### Post by Houman on 2006-12-18
> 
If you don't find you also have these problems, and can JUST get code completion at no cost, then congratulations. Really, keep using that tool. But those are some reasons why eclipse (and every other IDE I've used) annoys me (and possibly other people).


You are right on that one, no Linux IDE has yet gotten it right, some of them are just awful (cough* Anjuta cough*). I do miss Visual Studio, I mean if you let it do all the work for you you dont learn anything, but if you use its nice utilities without relying on its code generation services it will make things easier without spoiling the programming/learning experience. But im hoping Code::blocks will turn out good, I am keeping my fingers crossed.

> 
You did address the post to emacs users :P.


Hahaha :D  you totally nailed me on that one, i guess I was hopipng everyone would read it even though its only addressed to Emacs people :|


regards

Houman

---

### Post by raul_ on 2006-12-18
What's wrong with Eclipse? I like it =\ it's actually smarter than the Java compiler, but i just use it when i'm having a bad day or to keep my classes organized. I normally go with gVim

---


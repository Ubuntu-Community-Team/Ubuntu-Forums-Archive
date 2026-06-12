---
title: "PDT plugin for eclipse, code assist."
date: 2009-05-31
forum: Programming Talk
---

### Post by BramWillemsen on 2009-05-31
Hi everyone.

I recently started coding so I downloaded an IDE. Some people advised me to try eclipse. I downloaded eclipse and installed the PDT. Then i watched this tutorial: [http://www.youtube.com/watch?v=VRFZpk-YHl4](http://www.youtube.com/watch?v=VRFZpk-YHl4) . 

-At 6:31 I think he uses Code Assist. I exactly typed the same code as him. I type "$this->" without the quotation marks and wait for the Code Assist options to appear. Sometimes it appears, but in most cases nothing happens! i keep typing and removing "$this->" to see if the Code Assist appears but in most cases nothing happens. I am using the PHP perspective btw for my project. 

It's my first IDE so maybe i forgot something. Does anyone have an idea why the code assist acts so irregularly?. I cant seem to find out whats going wrong.

kind regards, Bram

---

### Post by BramWillemsen on 2009-06-01
hmm i tried reinstalling but im having no luck.

---

### Post by tyfius on 2009-06-01
The problem might be caused by the version you are currently using. I know that the latest stable release has some issues with it and you can read more about it [here]("http://spektom.blogspot.com/2009/05/var-magic-comment.html").

Using the @var comment is not a bad way in my perspective and it's supported by a variety of IDE's.

---

### Post by BramWillemsen on 2009-06-01
hi tyfius, thanks for your reply. I read the post and tried the first example. I typed the commented code and then did $test-> and waited for the Code assist to appear, but nothing happened ( [http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-PHP-testproject-newfilep.png](http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-PHP-testproject-newfilep.png) ). Or do you have to automatically generate those @var comments in order for them to work ?

My previous example from the youtube tutorial did work but only in like 25% of the cases. If i remove the line and retype it chances are big that no Code Assist window appears.
[http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-PHP-testproject-testfile.png](http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-PHP-testproject-testfile.png)

btw i first downloaded eclipse from their website. I then downloaded PDT from help->software updates suggested by the PDT installation guide [http://wiki.eclipse.org/PDT/Installation](http://wiki.eclipse.org/PDT/Installation) . I selected the PDT SDK 2.0.1 since there was no 2.0.0 like the installation guide suggested. [http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-SoftwareUpdatesandAdd-on.png](http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-SoftwareUpdatesandAdd-on.png) . Also installed the DLTK package suggested by the guide. 

Eclipse looks quite nice and i'd love to know more about it. But it seems like the @var comment did not solve the bug either. It's quite strange.

edit: it seems like more people suffer from this. I guess he describes something similar. [http://www.mail-archive.com/pdt-dev@eclipse.org/msg00339.html](http://www.mail-archive.com/pdt-dev@eclipse.org/msg00339.html)
> Hi,
>
> I have similar problem, code completition doesn't work for me
> everywhere, in some function doesn't work code asist for local
> variables, now i have project where code assist in 20% doesn't work,
> it's very frustration, after restart code assist work few min and then
> work only some cc

---

### Post by BramWillemsen on 2009-06-01
It's unfortunate that eclipse has no own forum to asks these things.

---

### Post by mdawg414 on 2009-06-01
You can press Ctrl->Space to bring up the Code Assist manually. Does doing that bring it up or still nothing?

---


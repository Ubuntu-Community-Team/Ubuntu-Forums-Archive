---
title: "Need help with a couple problems..."
date: 2008-05-17
forum: New to Ubuntu
---

### Post by ardvark71 on 2008-05-17
Hi...

Perhaps someone might lend me a hand....

1. I downloaded a tarball of Mozilla Thunderbird to my desktop and Ark will not open it up. It states some error prevented it from doing so but is not specific. Is there another tarball extractor I can download from the repositories that will do the job?

2. For some reason, my screensaver will not come up at all....it's set to automatically start after 10 minutes but doesn't. Does anyone have any ideas what to do to get it working?

Best Regards...

---

### Post by Paqman on 2008-05-17
Thunderbird is in the repos. You should always check the repos first for any software you want to install.

---

### Post by ardvark71 on 2008-05-17
> **Paqman said:**
> Thunderbird is in the repos. You should always check the repos first for any software you want to install.

Hi...

What is it under? I only saw the language packs.:confused:

Best Regards...

EDIT: Never mind....I found it! Anyone have any idea about the screensaver?

---

### Post by z0mbie on 2008-05-17
Type in to a terminal:

```
sudo aptitude install thunderbird
```

---

### Post by lescarlin on 2008-05-17
> **z0mbie said:**
> Type in to a terminal:

```
sudo aptitude install thunderbird
```

Jeez.  I been trying for ages to install my d/l of T/Bird.  Then i came across your terminal instruction.  OK, it worked fine, but apart from me getting familiar with the command-line method, is there not another method for installing this stuff? - i would have thought via synaptic or similar.  It really annoyed me to find the help system telling me .tar files should have a readme file, then when i opened the t/bird readme it referred me to the mozilla website, promising that this would tell me how to install t/bird.  No such luck.  Their website installation help just told me stuff about older installations being overwritten.

ok, rant over.  But this is really not good enough, being bounced around like that.  Thx for the help on this.

les

---

### Post by ardvark71 on 2008-05-17
Anyone have an idea concerning the screensaver?:confused:

Best Regards...

---

### Post by Sef on 2008-05-17
> Anyone have an idea concerning the screensaver?

Check the Screensaver.  Is the Screensaver set to Blank Screen? If so, change it to what you want.

---

### Post by ardvark71 on 2008-05-17
> **Sef said:**
> Check the Screensaver.  Is the Screensaver set to Blank Screen? If so, change it to what you want.

Hi...

Thanks for your reply, the fireworks saver is enabled and is supposed to come up in 10 minutes but never does.

Best Regards...

---

### Post by Paqman on 2008-05-18
> **lescarlin said:**
>  OK, it worked fine, but apart from me getting familiar with the command-line method, is there not another method for installing this stuff? - i would have thought via synaptic or similar.

Ubuntu's Advanced Packaging Tool, or APT, is the system behind the terminal commands "aptitude", "apt-get", as well as Synaptic, Add/Remove, Update Manager, etc. It's all the same system, with many different ways of interacting with it. 

People in the forums will often post the command line way of installing packages, because it works well in text.

---

### Post by rustutzman on 2008-05-18
> **ardvark71 said:**
> Anyone have an idea concerning the screensaver?:confused:

Best Regards...

I take it that your selected saver works fine in preview. If so I'd try the old Windows trick. Disable it (clear the checkbox) then close things up. Then go back in and enable it in the checkbox and close it up again and see if that works.

Russ

---

### Post by ardvark71 on 2008-05-19
> **rustutzman said:**
> I take it that your selected saver works fine in preview. If so I'd try the old Windows trick. Disable it (clear the checkbox) then close things up. Then go back in and enable it in the checkbox and close it up again and see if that works.

Russ

Thank you but no dice.:(

I'm at a loss to understand this.:confused:

Best Regards...

---


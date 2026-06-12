---
title: "Skype (P2P connect failed) in ubuntu 11.04"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by rrsk on 2012-03-02
Eventhough i did

> 
rm -rf ~/.Skype


skype is not worked properly for me in 11.04........

pls help me....

---

### Post by Ms. Daisy on 2012-03-03
Perhaps if you start at the beginning of the story it will make more sense.

How did you install Skype? From the Software Center?

What did you do after rm -rf'ing skype? (and who told you to do that?)

What exactly is not working properly? Does Skype start? Can you log in? Do you see your contacts? Can you make a call? Video working? etc. etc. etc.

---

### Post by rrsk on 2012-03-08
> **Ms. Daisy said:**
> Perhaps if you start at the beginning of the story it will make more sense.

How did you install Skype? From the Software Center?

What did you do after rm -rf'ing skype? (and who told you to do that?)

What exactly is not working properly? Does Skype start? Can you log in? Do you see your contacts? Can you make a call? Video working? etc. etc. etc.

i downloaded skype 2.2 beta .deb 64 bit .deb file from skype site...
and installed using "dpkg -i" command

as my title implies, when i am trying to sign in , it shows error "p2p connect failed"

when i tried in google , many threads said "do rm -rf ~/.Skype" for this problem and some said they can sign in after they did rm -rf ~/.Skype......

Thank u for your Response......
If you need , am ready to give you more info too....

---

### Post by Ms. Daisy on 2012-03-08
I'm afraid I don't know how to fix the downloaded version you used.  But you may want to consider removing the package you installed, then installing skype from the software center instead.

---

### Post by rrsk on 2012-03-08
> **Ms. Daisy said:**
> I'm afraid I don't know how to fix the downloaded version you used.  But you may want to consider removing the package you installed, then installing skype from the software center instead.

thanks for ur guide.....

just i want to let u know is

version: Skype 2.2.0.35-1 

whats problem with this version??
Can u elaborate?

---

### Post by winh8r on 2012-03-08
Go to the Ubuntu Software Centre and search for skype

select install

try it again.

It is not a good idea to go running the rm -rf command unless you actually know what it is going to remove. It is a very powerful command and can make your system completely unusable if you get it wrong. Always check out what a command does before you run it. 

Any command you want to know about, just open a terminal and type

man <name of command>

like this

```
man rm
```

Let us know how the skype reinstall goes.

Hope this is of some help to you.

---

### Post by Ms. Daisy on 2012-03-08
> **rrsk said:**
> version: Skype 2.2.0.35-1 
 
whats problem with this version??
Can u elaborate?
First, +1 to winh8r's comment.
 
To answer the question "what's the problem with this version?"-
Software Center is the preferred method to install sofware. It is designed specifically to make installation super simple. 
 
Here's a link which will explain in greater detail why the software center is the best way to go.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by luigli on 2012-03-10
I had the same problem. I didn't use Skype for a long time so i didn't realize it was no working till today. I have Ubuntu 11.10 64bits with Skype installation from Ubuntu repository. I just renamed .Skype directory and it worked again.

---

### Post by unc0nn3ct3d on 2012-03-12
Moving/renaming the entire skype directory can be overkill, usually you just need to delete the shared.xml file and you'll be good to go

---

### Post by ashwinchandrap on 2012-03-14
I did 'apt-get autoremove' to remove a package that was no longer used. After this, skype started working normally.

---


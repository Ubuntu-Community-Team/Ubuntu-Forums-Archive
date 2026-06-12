---
title: "Internet not conneting"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by gdookuk on 2013-06-02
Hi 
I am completly new to ubuntu.

I have 12.04 installed.

I have been trying to connect to the internet but with no success.

I have a Vivid wireless home gateway router which connects via an ethernet cable.
 
Can someone point in the right direction of where to start?

I can access the internet on a tablet computer via a wifi connection so i assume something needs to be configured in ubuntu for the wired connection to work?

Thanks
Graham

---

### Post by 3rdalbum on 2013-06-02
Nothing should need configuring. If it's connected through Ethernet, Ubuntu should just start the connection straight away without you having to do anything.

Try plugging in the Ethernet cable and going to the terminal (hit Control-Alt-T) and type or copy and paste the following:

```
ifconfig
lspci
```

(the last one is "LSPCi" but all lowercase)

Paste the results into a reply to this message and we'll see what might be happening.

---

### Post by gdookuk on 2013-06-02
Thanks. for responding.

But the problem was I am an idiot. My ethernet cable was unplugged!!:oops:

I am going to go and die quietly of shame. And next time check all the basics first.

Cheers

Graham

---

### Post by squakie on 2013-06-02
Hey, don't feel bad - we've all been htere!

---


---
title: "New Ubuntu 8.04 install.....need help installing X-Fi drivers....."
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Sipster on 2008-07-02
Hey guys.  Brand new to Linux user here.  Did clean install of 8.04 and everything is working fine except I have no sound.  I have a Creative X-Fi Extreme Music sound card. I've downloaded the beta drivers from Creative's web site but can't figure out how to install.  I am a total Newbie.

Please help!

---

### Post by iaculallad on 2008-07-02
> **Sipster said:**
> Hey guys.  Brand new to Linux user here.  Did clean install of 8.04 and everything is working fine except I have no sound.  I have a Creative X-Fi Extreme Music sound card. I've downloaded the beta drivers from Creative's web site but can't figure out how to install.  I am a total Newbie.

Please help!

On your terminal, issue the command below and post the result:

```
asoundconf list
```

---

### Post by Sipster on 2008-07-02
> **iaculallad said:**
> On your terminal, issue the command below and post the result:

```
asoundconf list
```


Yeah, I read that in another forum but nothing comes up for me when I try that.

---

### Post by iaculallad on 2008-07-02
> **Sipster said:**
> Yeah, I read that in another forum but nothing comes up for me when I try that.

That only means that it cannot detect your sound card so there's no sound coming up from your system.

If by chance, does your motherboard come with built-in sound card?

---

### Post by Sipster on 2008-07-02
Yes, my mobo does have onboard sound but I am dual booting with Vista so I don't really want to turn that on.

---

### Post by iaculallad on 2008-07-02
> **Sipster said:**
> Yes, my mobo does have onboard sound but I am dual booting with Vista so I don't really want to turn that on.

Does the terminal command **asoundconf list** display nothing at all?

```
asoundconf list
```

or

```
lspci | grep audio
```

---

### Post by Sipster on 2008-07-02
adoundconf list - shows nothing

lspci | grep audio - shows "Multimedia audio controller: Creative Labs SB X-Fi"

---


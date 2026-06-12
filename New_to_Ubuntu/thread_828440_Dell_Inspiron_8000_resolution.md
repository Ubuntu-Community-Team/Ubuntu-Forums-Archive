---
title: "Dell Inspiron 8000 resolution"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Acadia on 2008-06-13
Hi everyone - I have read every thread and tried everything I can to get higher than 800 x 600 resolution on my Ubuntu installation on my Dell Inspiron 8000.

I have somehow gotten it to a state where when I start up it says: we cannot detect your graphics card or monitor!

But when I try to get it to detect anything it says it can't and then it brings me to the command prompt window.

So now I am worse off than I was before - should I start over?

Should I give up?

I don't get how when I first boot up the UBUNTU logo thing looks nice and normal, but after that it all goes to heck.

Please advise if I should kill myself.  Thanks!

---

### Post by Acadia on 2008-06-13
OK - so now it goes to the regular screen but it is only 640 x 480.  I am not sure this is better

=/

---

### Post by _sphinx_ on 2008-06-13
Okay lets' start with the situation in which you are now. What kind of command prompt window you are in? Is it tty, I mean is it just a black sort of thing with nothing except a terminal sort of thing? If it, is then I think you should try pressing Alt+Ctrl+F7, If it doesnt' work press Alt+Ctrl+F1, login there and type 
```
sudo gdm
```
I think it should give back your 800 x 600

---

### Post by _sphinx_ on 2008-06-13
OK that an good achievement. Any ways let's work on your resolution now. Have you read something on net about Dell Laptop resolution on ubuntu. If you have than you must know about a pacakage named 915resolution or something similar to that. I am just searching, I will let you know if I found something about how to use.

---

### Post by Acadia on 2008-06-13
Thanks so much, _sphinx_.

Right now, I am apparently downloading 44 updates, so I can't do anything.

There is a thread on these forums about this specific laptop - but I did not have the same issues those guys had, and I tried to copy what they said to do but had no luck.

---

### Post by _sphinx_ on 2008-06-13
I am saying you to install 915resolution because I also have Dell Inspiron and used to have a sort of similar problem that you are facing now but I think Hardy version has solved this bug, any ways you should install 915resolution and see if it works. I found a link for the readme for 915resolution.
[http://www.geocities.com/stomljen/readme.html](http://www.geocities.com/stomljen/readme.html)
But I can make make long thing short for you:
```

sudo apt-get install 915resolution
sudo 915resolution -l

```
See the list of resolutions and number corresponding to them. Choose number corresponding worst resolution(that you don't want to use) then do following.
instead of 58 use your selected number and instead of 1280 800 choose the default maximum resolution
```

sudo 915resolution 58 1280 800
sudo gedit /etc/default/915resolution

```
In /etc/default/915resolution, I think you have to edit at 4 palces, two for x and y resolution, one for depth which you should fill 32 and last is the selected number.

Maybe I am wrong at some place but then you should keep readme as the first option. I am just trying to remember what I used to do.

---

### Post by Acadia on 2008-06-13
It says wrong chipset detected

i suck

---

### Post by _sphinx_ on 2008-06-14
When does it says this?

---


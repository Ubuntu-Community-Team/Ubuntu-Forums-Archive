---
title: "Keyboard numberpad/scroll lock woes."
date: 2011-10-24
forum: New to Ubuntu
---

### Post by ouija1979 on 2011-10-24
Got a new basic keyboard and for some reason the number lock won't work and the number pad is controlling the cursor, it is extremely frustrating. I got it to replace my light-up keyboard, because for some reason, there is no way in ubuntu to get the scroll lock working by default, and the scroll key is what lit the keyboard up. I am quite angry at the moment so excuse my rambling, I am no programmer but basic keyboard support by default should be a priority. I have basically wasted money buying keyboards, and I would love if someone could help me get this number pad thing sorted. 

The only way I could get my keyboard to light up was to type "xset led on" in the terminal, but I shouldn't have to do that every time I log in, is there anyway to get a scroll lock key working by default? The odd thing is that when ubuntu is starting up, I can hit the scroll key and it works perfectly, but when 11.10 has fully started it refuses to work, it has me scratching my head.

Basically 2 separate problems I know. Please help, the keyboard wasn't exactly cheap.. ;)

---

### Post by sanderd17 on 2011-10-24
To execute a custom command at login, you should place it in your .profile file.

Just do
```

gedit .profile

```

in a terminal. And in that file, type
```

#! /bin/bash
xset led on

```

And for the other things, can you give the types of your keyboard, they seem quite special.

Maybe something you can try for the numlock: install numlockx. You probably also have to run it.

---

### Post by ouija1979 on 2011-10-24
Thanks, it all lights up now :) The light up keyboard is called "Little Kangaroo LED" and my other one is a "Logitech K200" both keyboards are doing the odd number pad thing, I have went into the setting and restored defaults, I was using an aluminum Mac keyboard before buying these and it was working fine... The 2,4,6 and 8 keys are all moving the cursor. and the number lock button won't work.

---

### Post by sanderd17 on 2011-10-24
If they both have the problem, it must be a setting.

Are you using Oneiric (11.10)? If so, go to the system settings (I don't know exactly where it is in Unity), and check out "universal access". This are the accessibility options. Under "pointing and clicking" there should be a setting to control your mouse with your keyboard. Make sure it's not checked. 

It should be under "mouse" or "keyboard" options too, but it's considered as an accessibility option.

I think I'm going to file a bug for this.

---

### Post by ouija1979 on 2011-10-24
Thanks, that worked. I was in all the other Keyboard settings and nothing, I have no idea how it became checked. Thank you for your help, I now have a funky blue LED keyboard with a working number pad. ;) The number lock key isn't working still, but that's ok, as long as the number pad is working.

---

### Post by sanderd17 on 2011-10-24
No problem, please mark your thread as [SOLVED].

---


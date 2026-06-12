---
title: "Advanced keyboard mapping in xmodmap?"
date: 2010-06-18
forum: Programming Talk
---

### Post by doccer on 2010-06-18
I'm quite new with Ubuntu and now I'm looking for possiblity to make keyboard macros/mapping.
I found out that I should use tool called xmodmap, right?

If there are anyone with experience, can you please tell me how to make following binding:

- Whenever I press button "å" it will be lauch button "alt gr"
- Whenver I pres button å + and the same time "d", it will be output "{"
- Whenver I pres button å + and the same time "f", it will be output "}"
- Whenver I pres button å + and the same time "v", it will be output "$"
...and so on, I can fix it  and make more if just somebody give me idea.

I would be very thankfull if somebody help me becouse it would give me a possibilty to code much faster
becouse I'm very used to use that type of mapping in Windows.

---

### Post by lykeion on 2010-06-18
Ok, I haven't tried this before but after a few searches in th forums I found out this:

1. You can get the keycode for a key with xev (install x11-utils)
Start xev from a terminal and type your key (å -> keycode 34)

2. Use xmodmap to change key mappings. Check the man page. This is an example:
xmodmap -e 'keycode 34=Alt_R' 

3. Create a bash script to hold your mappings so you can easily execute these mappings at startup or before you start coding.

Hope this helps

---

### Post by doccer on 2010-06-18
Thank you a lot for giving me your time!

I'm gonna research about that and if there are more problems, I will ask here again.
Looks like quite clear plan, just Im wondering how it is possible to make key combinations becouse if i just 
press "f" it should print f, but "alt gr" or "å" + "f" should output }.


Thanks dude!

---


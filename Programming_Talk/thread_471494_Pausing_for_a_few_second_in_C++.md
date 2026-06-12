---
title: "Pausing for a few second in C++"
date: 2007-06-12
forum: Programming Talk
---

### Post by King_Critter on 2007-06-12
Well, I just (like, yesterday :P)  started learning C++. It's pretty cool, as I've got a [nice tutorial]("http://www.isotton.com/lcpp.html") to help me out. However, there's one thing I just can't figure out...

One of the examples the afore-mentioned tutorial has is a simple calculator program. You choose wether you want to add or multiply, then you put two mumbers in and it gives you the answer. I decided to take this and make it cooler, as a test of what I'd learned so far. The main thing I added (well, *tried* to add) is a little thing that comes up when you select an option. It'd say something like "Initalizing mathematical subsystems." (partly inspired by the [Hax0r script]("http://ubuntuforums.org/showthread.php?t=470386") ;)) It would then start spamming periods for a bit like it was laoding something, then say "DONE" and continue on with the rest of the program. 

However (and this where the problem appears) I need something that will make a pause between each period for a a fraction of a second. I little bit of Googling found me "sleep()" but either I'm using it incorectly or something's wrong, because it just hangs for a bit then prints all the periods at the same time. Not exactly what I'm going for. Here's my code (the part that matters, anyways.)

```
	if (selection == 1) {
			int i = 0;
			while (i < 15) {		
				cout << ".";
				i = i + 1;
				sleep(250);
			}
```


Can anyone help me out here?

---

### Post by bboozzoo on 2007-06-12
```

std::cout << '.' << std::flush;
i++;
sleep(250);  // really sleep 250s?

```
sleep works for sleep times in range of seconds, you might want to use usleep instead

---

### Post by joe_bruin on 2007-06-12
[looks like the previous poster did a better job than I and in far less words.  next time, i will read before writing.]

---


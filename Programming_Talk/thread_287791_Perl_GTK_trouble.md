---
title: "Perl GTK trouble"
date: 2006-10-29
forum: Programming Talk
---

### Post by Engnome on 2006-10-29
Anyone knows why the following snippet doesn't change the image?

```

if($i == 1)
	{
	$image2->set_from_file('2a.jpg');
	sleep(0.5);
	$image2->set_from_file('2b.jpg');
	}

```

Been googling and looknig at manual tutorials and stuff but came up with nothing. Helping me will (hopefully) result in me posting a small GTK game as a thanks.

---

### Post by Engnome on 2006-10-29
Oh never mind, the usual thing happened. I walked away from my keyboard and a few hours later I suddenly realised that the gui probably only updates when the program waits for events in ```
Gtk2->main;
```

Guess I'll have to find some way to update the gui somehow or run multiple threads or something like that, never tried that before.

Edit: Found this: [http://spr.mahonri5.net/gtk2-perl-tutorial/](http://spr.mahonri5.net/gtk2-perl-tutorial/)

---

### Post by Engnome on 2006-10-31
Hopefully someone having the same problem as I will find this thread and benefit from my monolog. :) 

Anyway I decided to post my game. Any comments about my programming? Constructive criticism is very welcome. :KS

---


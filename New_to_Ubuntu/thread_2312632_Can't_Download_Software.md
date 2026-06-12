---
title: "Can't Download Software"
date: 2016-02-05
forum: New to Ubuntu
---

### Post by Dying_Starman on 2016-02-05
[COLOR=#000000]Hello. I am relatively new to Ubuntu. Recently, I tried to download Spotify, and I got this message after I executed the download commands:[/COLOR]
[COLOR=#000000]SystemError: E:Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.list[/COLOR]

[COLOR=#000000]Just thinking this was my usual bad luck, I moved on. Now I can't open the Software Center(Whenever I try it just opens and closes instantly), I can't download anything else (I get the same error message after I execute the commands in the terminal), and I get an error message in the top right every time I boot up saying the same thing as before. Can anyone help me?[/COLOR]

---

### Post by grahammechanical on 2016-02-05
Can you show us the exact command or commands that you ran?

I guess that if you uninstalled Spotify or removed spotify.list then the problem would go away. Whenever we load Ubuntu the update manager will after a few minutes check for updates. It will access all the files that record the URLs of the software sources. I am guessing that when it gets to spotify.list it is detecting that error in the first line of the file and then tripping up.

Knowing the commands that you used and also seeing the contents of spotify.list might help.

Regards.

---

### Post by Dying_Starman on 2016-02-05
This are the commands I used (They are the official ones from the Spotify website. I list them from first to last):
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886

echo deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list

sudo apt-get update

sudo apt-get install spotify-client

---

### Post by Vladlenin5000 on 2016-02-06
When posting code please use the Go Advanced button, click # and paste inside.

That said, I just tested and it's correct. So, you must have typed something wrong...

Doing
```
[COLOR=#000000]cat /etc/apt/sources.list.d/spotify.list[/COLOR]
```
should give this result:
```
deb http://repository.spotify.com stable non-free
```

Please show us yours.

---

### Post by Dying_Starman on 2016-02-06
OK so I actually tried installing Spotify about a month ago(a few days after I got Ubuntu- my first Linux experience) so honestly I didn't remember the exact things it said. So I tried the code again and it works! The error message also went away. I'm gonna reboot and see if it pops up again. Also, I did not know that about the code. Still learning.  Thank you!

---

### Post by Bucky Ball on 2016-02-06
If it doesn't pop up again, please see the first link in my signature and mark thread as solved. Thanks.

The easiest thing to do is to transfer code with copy/paste. To copy into a terminal, you use control+shift+c and for paste same but with 'v', or use the 'Edit' drop-down menu. That way there can be no typos. :)

Good luck and enjoy.

---


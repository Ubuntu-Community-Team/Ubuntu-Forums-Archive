---
title: "nautilus displaying &quot;old&quot;looking? installed clamscan, may it be the cause?"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by freedback on 2011-11-01
Hello community!

I came to have this kind of "old-looking" (if thats the right way to call it) that I attach here...well, when asking to empty the recycle bin...you can see in the other attachment..it is clearly weird look, isnt it?

I dont know what to associate it but it must be smth related to nautilus, right?

And it started (I think) when I tried installing (wrongly) a complement/plug-in to nautilus about clamscan.

Thats the data I can give ...I dont know if anything else could help?
What I would want to know is how can I recover my much more nice oneiric-looking nautilus...and by the way, I cant never totally empty recycle bin (it always looks as if it had any files inside...has it anything to do with it?, can I fix it to be empty when it actually is actually empty? )

---

### Post by dFlyer on 2011-11-01
I don't see anything strange about your pop up box to empty trash except it's not in english. As far as not being able to empty trash have you tried going to you Trash folder?

cd /.local/share/Trash

you will have three folders in there. You can cd into each folder and delete any files with:

rm -rf .* *.*

That may solve your trash not emptying problem.

---

### Post by freedback on 2011-11-01
:D ....sorry about spanish legends 
and thanks for helping!

Actually I did the cd and there it says not such directory or file exists :confused: ...I tried to check and it goes until last level (thats "share" folder) all ok.. and tried to list down there (in the same "usr/local/share" folder) the files/folders inside and in blue letters it answers these: 
*ca-certificates; fonts; man; ppd; sgml; texmf; xml*  

Any idea whats that about? Im very sure that the very only "hesitant" move I made was installing that "clamscan" extension to nautilus....but I think it made smth in there..or maybe its dependencies?
I checked this "clamscan" dependencies (at synaptic) and shows me this: 

```
Package: nautilus-clamscan - version: 0.2.2-2.1
```

and within "dependencies" tab of the "properties" in contextual menu, gives me back:
```

-python
-python-central (>=0.6.11)
-python-gtk2
-python-clamav
-python-nautilus
```

Indeed, Im not only worried about recicle bin, though may be I can manage without it (but is not normal, is it?) ...Im also very concerned about the true integrity/malfuncioning, or whatever at nautilus...starting on the fact it looks different

Every possible help anyone can give there, Ill be totally thankful!!
Thousand thanks!

---

### Post by freedback on 2011-11-02
Hello everyone who reads this...
I had yesterday some udpates (of nautilus among others) and installed them, asked me to restart, and done, I attach the screen of the nice result.

I was very happy, til I realized that after some while nautilus looked the same again ...
I had tried sending some files to reciclebin/trash and emptying it, and could succesfully, tried again now, and ok too.
So in one hand, this reciclebin issue is solved. Thanks to dFlyer for helping :)

...Then I restarted computer again and nautilus ok again...but once again, just for some while.

Went to synaptic...uninstalled the extension I thought was the one giving troubles nautilus-clamscan, and conitues the same.

No idea what else I should do...where is controlled/set-up nautilus from?
What can I check/do to make it work like it should?

Totally thanks!!

---

### Post by dFlyer on 2011-11-02
Start synaptic and mark nautilus for reinstall and see if that helps. You may also search your home folder for nautilus and move your nautilus folder to nautilus.old before you reinstall nautilus. From the command line enter the following:

sudo updatedb

locate nautilus

This will list the folder that nautilus in your home and only your home folder then making sure your in the folders nautilus is located in.

mv /home/yourname/.config/nautilus /home/yourname/.config/nautilus.old
mv /home/yourname/.gconf/apps/nautilus /home/yourname/.gconf/nautilus.old
mv /home/yourname/.gnome2/.nautilus-scripts /home/yourname/.gnome2/nautilus-script.old
mv /home/yourname/.gnome2/accels/nautilus /home/yourname/.gnome2/nautilus.old

Hope this helps.

---


---
title: "Done something bad concerning permissions and root"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-09-16
I seem to have messed things up a bit by trying to do things I didn't understand. 

I was trying to delete a folder (that was previously a back up of my home folder) because I'd run out of space. I found I couldn't just put it in the trash bin. So I changed the ownership in order to change the permissions. I used chown to change permissions. Then just right clicked on the folder and changed everything to "read and write". 

Then I used 
sudo rm -r /home_backup
to delete it. 

It seemed to delete just fine. 

However, a few bad things have happened since then. Webpages (this one included are looking very simple). My wallpaper has disappeared. And I can't start any programmes, receiving the error

 Could not launch menu item. 
Failed to change to directory '/home/james' (Permission denied)

I am hoping people can help me quickly because I have a feeling if I try to reboot it won't allow me to log back in. 

Thanks, 
James

---

### Post by iaculallad on 2008-09-16
Try doing this:

```
sudo chmod 755 /home/james
sudo chown james /home/james
```

---

### Post by pmlxuser on 2008-09-16
sudo rm -r /home_backup

that looks very dangerous. 
try
```

sudo chown james:james /home/james

```
however let me say if you made a mistake of putting an asterick (*) withon your 
```

sudo rm -r 

```
command you will have a very big problem.

---

### Post by Jimmy9pints on 2008-09-16
Thank you iaculallad and pmlxuser for your responses. 

I can't open the terminal. 

Clicking the icon causes the aforementioned error and alt+f2 gnome-terminal just does nothing. 

FYI pmlxuser I didn't put an asterix. 

Cheers,
James

---

### Post by mikewhatever on 2008-09-16
Try using the recovery mode (usually the second boot option). You might want to write down the commands to enter, since there is no GUI in recovery.

---

### Post by Jimmy9pints on 2008-09-16
OK recovery mode it is, but which is correct?

sudo chown james:james /home/james
or 
sudo chown james /home/james

?

---

### Post by iaculallad on 2008-09-16
> **Jimmy9pints said:**
> OK recovery mode it is, but which is correct?

sudo chown james:james /home/james
or 
sudo chown james /home/james

?

Both commands mean the same thing.

EDIT:

> sudo chown james:james /home/james

Command means, let james own /home/james, and make james a member of james group.

> sudo chown james /home/james

Command means, let james own /home/james folder. (Explicit as james only owns the james folder and does not need the group james).

---

### Post by Mornedhel on 2008-09-16
> **iaculallad said:**
> Both commands mean the same thing.

I'm probably being pedantic here, but chown james means "change owner to james", while chown james:james means "change owner and group ownership to james". I'm sure you were aware of this, but I still think it's worth mentioning.

Edition : OK, being pedantic after all, sorry.

---

### Post by iaculallad on 2008-09-16
> **Mornedhel said:**
> I'm probably being pedantic here, but chown james means "change owner to james", while chown james:james means "change owner and group ownership to james". I'm sure you were aware of this, but I still think it's worth mentioning.

Yes, I am aware of that. The reason why I edited my post before you posted so as to clear what I meant with "Both command mean the same thing".

---

### Post by The Cog on 2008-09-16
It is just possible that /home/james has been deleted entirely (typing error possibly). Check this in recovery mode with:
```
ls -l /home
```
and see if james is listed. If not, do:
```
mkdir /home/james
chown james:james /home/james
```
but of course all your data will have gone.

---

### Post by Jimmy9pints on 2008-09-16
OK I tried to reboot and as I expected, it didn't let me log in. 

I tried a failsafe session but it wouldn't accept my password when trying to run those commands you gave me. Strange, because I know my password very well. 

Now I am running a live CD session. 

Browsing the files I can see that all the files that were in home/james/ have gone! Dam!

Leaving me two options:

1.Reinstall
2. Restore this directory from a much earlier backup (about 2 or 3 months ago when running Gutsy)

However, I don't really know how to go for option 2 since in this live CD session I do not have permissions to move files around or write to the directory I want to restore. 

Baffled...James

---

### Post by MegaJim on 2008-09-16
Did you try to login as "james" or as "root".

Logging in as "root" should still work, unless the remove did more than delete the home directories

---

### Post by pmlxuser on 2008-09-17
> **Jimmy9pints said:**
> 

Now I am running a live CD session. 


 since in this live CD session I do not have permissions to move files around or write to the directory I want to restore. 

Baffled...James

Please do

```

sudo nautilus /home

```

you will have access to move or create a folder in that.

and then you could do the other things

Or Just do a copy the backup files to some medium after executing the above command.

Do clean install

place your files in your new account

enjoy ;)

---


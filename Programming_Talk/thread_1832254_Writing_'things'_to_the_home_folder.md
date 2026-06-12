---
title: "Writing 'things' to the home folder"
date: 2011-08-24
forum: Programming Talk
---

### Post by mendhak on 2011-08-24
I've noticed that a lot of apps create hidden directory in the user's home folder.  For example, 

/home/mendhak/.minecraft

Is this considered the proper way to do things?  

Is it considered bad if I want to use my application directory itself to store the temporary files and configuration files?

---

### Post by lykwydchykyn on 2011-08-24
Typically:
 - /etc is used for system-wide configs that affect all users
 - hidden files and folders in a user's directory are typically used for user-specific configurations.  Some programs create a directory in ~/.config or ~/.local instead.

Putting these things in the program's (binary files) directory is bad design from a Unix standpoint, because it will require that the program's directory be writable.

---

### Post by mendhak on 2011-08-24
> **lykwydchykyn said:**
> 
Putting these things in the program's (binary files) directory is bad design from a Unix standpoint, because it will require that the program's directory be writable.

Good point, I hadn't thought of that.  It would not immediately be obvious to the user where the configuration file is, though.  This appears to be a motivation for good UI that can cover all the options.

---

### Post by JupiterV2 on 2011-08-24
I believe that using a user's home directory is the accepted practice. I may be wrong, so someone correct me if I am, but there are potential security/permission concerns when storing configuration data outside of a directory a user may or may not have read/write access to. Second, this method provides a simple method of having per-user configuration settings since multi-user setups are backbone of Unix/Linux. Alternatively, if you are creating a GNOME application you can use the gconf or gsettings daemon to store per user configuration data. Incidentally, both gconf and gsettings use the user's home directory to store their data.

Lastly, I think system wide application data should be stored in /etc but I'm not 100% of this and am too lazy to look it up right now.

---

### Post by Smart Viking on 2011-08-24
The best is to use a hidden folder in the home directory IMO for configuration files and such, when people use GNU/Linux after a while they know that the configuration files are probably there. You can also have a system wide configuration file in addition, that can be handy for computers with many users.

---

### Post by lykwydchykyn on 2011-08-24
> **mendhak said:**
> Good point, I hadn't thought of that.  It would not immediately be obvious to the user where the configuration file is, though.  This appears to be a motivation for good UI that can cover all the options.

If the user is at all familiar with Linux, the conventions I mentioned should be familiar to them.  Anything else would be counter-intuitive.  

If they're not familiar enough to know those conventions, they probably aren't into hand-hacking config files.

---

### Post by Smart Viking on 2011-08-24
> **lykwydchykyn said:**
> 
If they're not familiar enough to know those conventions, they probably aren't into hand-hacking config files.
+1 to that, it's not like it's hard to find out.

---

### Post by mendhak on 2011-08-24
Everyone, thanks for your input, much appreciated.  The gconf/gsettings daemon sound useful too, I will read more about this.

---


---
title: "Post Install Script Question"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Xgen on 2011-08-26
How would I add the conky hardcore ppa to my post install script in oneiric with natty as the distro instead of oneiric...I reinstall frequently for testing.

---

### Post by lucazade on 2011-08-26
```
sudo add-apt-repository "deb http://ppa.launchpad.net/conkyhre/ppa/ubuntu natty main"
```

---

### Post by Xgen on 2011-08-26
Thanks Lucazade for the quick response...as usual it was something simple. I have most of my script in place, but some things I still do manually every time. Such as:

How to append:

[COLOR="Red"]UUID=e0aab1a9-571e-4f5c-a7be-73485e3b1aac  	/media/Linshare 	    	ext4    	defaults        	0	0

UUID=5341a3fc-fc07-421c-9f82-4039d98748e5	  	/media/Saved		    	ext4    	defaults        	0	0

UUID=c2f353b5-e0b6-4f73-b6fe-44b80f2b0be0	  	/media/Backups		ext4    	defaults        	0	0
[/COLOR]
-to the end of my fstab file?

---

### Post by lucazade on 2011-08-26
```
echo "UUID=e0aab1a9-571e-4f5c-a7be-73485e3b1aac  	/media/Linshare 	    	ext4    	defaults        	0	0
UUID=5341a3fc-fc07-421c-9f82-4039d98748e5	  	/media/Saved		    	ext4    	defaults        	0	0
UUID=c2f353b5-e0b6-4f73-b6fe-44b80f2b0be0	  	/media/Backups		ext4    	defaults        	0	0" | sudo tee -a /etc/fstab
```

anything else? :)

---

### Post by Xgen on 2011-08-26
Nah...I just had a lazy moment. Normally, I just Google the answer myself. Thank you for your indulgence :D.

---


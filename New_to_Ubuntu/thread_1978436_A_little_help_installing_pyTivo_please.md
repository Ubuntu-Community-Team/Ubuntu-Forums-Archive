---
title: "A little help installing pyTivo please"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by DrewLGT on 2012-05-11
So after much googling, i was able to install pytivo. I'm having trouble with the script to run as daemon, and the media path in the config file.

I have my videos in my downloads folder, so i set the path as: /downloads, I see the folder in my now playing list on the tivo, but it shows empty (it isnt). what should the path be?

when i try to make pytivo run as daemon i have an issue saving the init.d script in the /etc/init.d directory. i think the permissions are set to prevent me from writing to that dir. how can i change them?

thanks for any help you can give me

---

### Post by cariboo on 2012-05-11
Linux based distributions are case sensitive, and you may need the complete path to your downloads directory, it should look something like this:

```
/home/$USER/Downloads
```

Where $USER = your user name.

---


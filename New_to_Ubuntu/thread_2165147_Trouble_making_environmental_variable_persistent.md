---
title: "Trouble making environmental variable persistent"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by emerson1979 on 2013-08-03
Hello Everone
                      I'm having difficulty adding a directory to the PATH variable. I can successfully add the directory, but after I reboot it isn't there. I  issued the following command, "PATH=$PATH:/var/opt" I looked.  into a few configuration files such as "etc/profile; ~/..bashrc; and ~/.bash_profile. I also issued a command "export PATH" I have a book that tells me how to do this but it is of no help. I'm doing this just for practice as I'm teaching myself linux. Any help would be greatly appreciated.

Thanks

---

### Post by drmrgd on 2013-08-03
Did you have a look at this already?

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

If you want that variable to be system wide, the recommended way is to add it to /etc/environment according to this.  But note, that when you issue sudo, it doesn't use the the same environment and the change won't be reflected in that pseudo-session I believe.

---


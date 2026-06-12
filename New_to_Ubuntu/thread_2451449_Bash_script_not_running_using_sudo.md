---
title: "Bash script not running using sudo"
date: 2020-10-04
forum: New to Ubuntu
---

### Post by kevinmortimer on 2020-10-04
Hi All

I am a newbie to Ubuntu. I have managed to get my Ubuntu server instance with AWS started. I am able to connect using SSH. I am trying to run a command line that installs a package from githup. I am running as sudo but still get error that "bash must be run as root". Can anyone advise and assist?

Many thanks

---

### Post by scorp123 on 2020-10-04
> **kevinmortimer said:**
> 
"bash must be run as root"
Many thanks

With *that *syntax you're running the "wget" as root, not the script you're downloading.

Do it in 2 steps. First the wget + URL, nothing else after that, no pipe " | bash" nothing. After "wget" has finished the script you downloaded should be locally available, in whatever directory you happened to be in at that moment. Execute it now with:
```

sudo ./NameOfThatStuffYouDownloaded.sh

```

That should be running as root now.

---

### Post by kevinmortimer on 2020-10-05
Thanks so much for the explanation. 

The download seems to work fine but trying to run the installer gave errors. I tried checking the directory i was in using pwd and also used ls -lrt to check contents of current directory. The file appears to be there but i am unable to run it. I keep getting error "command not found" or "directory not found"

---

### Post by agvantibo on 2020-10-05
Try ```
sudo bash yourscriptname.sh
```

---

### Post by Impavidus on 2020-10-05
There are absolute paths and relative paths. Absolute paths start with a / or with anything that's shorthand for something that starts with / and are interpreted relative to the root of the filesystem. All other paths are relative paths and are interpreted relative to the current directory.

./G999_installer.sh is a relative path. With the file present in the current directory (as it is, according to ls), it should work, except for one thing.
/G999_installer.sh is an absolute path. With that sudo will look for the file in the root directory, where it won't find it.
home/ubuntu/G999_installer.sh is a relative path. With that file being where it is, that path only works if your current directory is the root directory. Adding a / at the start will turn it into an absolute path, which again should work.

There is a different problem though. To execute the file, you have to set execute permission on it if you want to run it directly from command line or from sudo. Use chmod. If you run bash with a command line argument to tell it to run this file (as in the suggestion above), you don't need that execute permission.

On a separate note, run as few programs with sudo as possible and be particularly careful with web-facing programs. There was no need to run wget with sudo. It also gave you a root-owned file in a place where you don't want root-owned files.

Required reading for every Linux-beginner: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ActionParsnip on 2020-10-05
The only part of your command with root access is the wget part. The script was ran as your user

---

### Post by scorp123 on 2020-10-05
> **kevinmortimer said:**
>  I keep getting error "command not found" or "directory not found"

"Execute" permissions are not there. The other guys in this thread already gave you solutions. Either do a:
```
sudo bash ./yourScript.sh
```

... or fix the permissions:
```

chmod 755 ./yourScriptG999whatever
sudo ./yourScript.sh
```

Also as was already explained to you: You can't make up paths as you want. There's an enormous difference between "**./**" (which basically means "right here in this directoy") and "**/**" which is the "root" filesystem, where everything else is attached to. Same thing with leading slashes: There's a difference between "/path/directory/sub-dir" and "path/directory/sub-dir".  The first one means that "/path" is attached directly to the root directory "/" and is underneath it, just like /etc, /home, /bin and all those other places there. The second one "path/directory" means that "path" is a relative path of some other location.  Don't ever mix those things up please!

See the explanations above that the other guys gave you.

---

### Post by kevinmortimer on 2020-10-06
Thanks for all your input

---

### Post by math492m on 2020-10-07
maybe try logging in as superuser "sudo su" before running the script?

---

### Post by ActionParsnip on 2020-10-07
> **math492m said:**
> maybe try logging in as superuser "sudo su" before running the script?

That's not "logging in as superuser". That's becoming root. There is no "superuser" in Ubuntu by default.

---


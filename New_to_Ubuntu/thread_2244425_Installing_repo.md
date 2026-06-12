---
title: "Installing repo"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by easysidedk.brydsko on 2014-09-16
Okay, so to set up this git repo, I need the "repo" command to work, therefor I went to [http://source.android.com/source/downloading.html](http://source.android.com/source/downloading.html) to find out how to download, so when I tried to do
```
[COLOR=#000000]curl https[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#880000]//storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo[/COLOR]
``` it came with the error that ```
bash: /home/dev/bin/repo: Permission denied
```
So I created the "repo" directory via ```
sudo mkdir home/dev/bin/repo
``` which worked, then I downloaded the repo file manually, and moved it via ```
sudo mr -r -f home/dev/Downloads/repo home/dev/bin/repo
``` which also worked fine, this didn't make the "repo" command work, I suppose this was due to the wrong permissions set up for the file? So I did ```
[COLOR=#000000]chmod a[/COLOR][COLOR=#666600]+[/COLOR][COLOR=#000000]x [/COLOR][COLOR=#666600]~[/COLOR][COLOR=#008800]/bin/[/COLOR][COLOR=#000000]repo[/COLOR]
```, which didn't give any respons and still the repo didn't work. 
So right now, I've removed the repo directory again and I'm back at the begginging... 
I can't seem to make either of the ways to work, and following the guide on android.com at doing this doesn't work neither even tho I've made sure /bin is in my home directory. Also the ```
[COLOR=#008800]$ PATH=~/[/COLOR][COLOR=#000000]bin[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#000000]$PATH[/COLOR]
``` which it tells me to do seems confusing to me? I did type that command before I did the ```
[COLOR=#000000]curl https[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#880000]//storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo[/COLOR]
``` command.
Any ideas on how to get this repo command installed ? 
I'm running Ubuntu 12.04 LTS by the way.

---

### Post by matt_symes on 2014-09-16
Hi

I have a bin directory already.

```
matthew-laptop:/home/matthew:5 % ls -d ~/bin
/home/matthew/bin@
matthew-laptop:/home/matthew:5 % 
```

I can download the repo.

```
matthew-laptop:/home/matthew:5 % curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 24081  100 24081    0     0  22928      0  0:00:01  0:00:01 --:--:-- 22956
matthew-laptop:/home/matthew:5 % 
```

It's a pythn script but not executable.

```
matthew-laptop:/home/matthew:5 % file ~/bin/repo && ls -l ~/bin/repo 
/home/matthew/bin/repo: Python script, ASCII text executable
-rw-rw-r-- 1 matthew matthew 24081 Sep 16 15:58 /home/matthew/bin/repo
matthew-laptop:/home/matthew:5 %
```

I can make it executable.
```

matthew-laptop:/home/matthew:5 % chmod 755 ~/bin/repo&& ls -l ~/bin/repo 
-rwxr-xr-x 1 matthew matthew 24081 Sep 16 15:58 /home/matthew/bin/repo*
matthew-laptop:/home/matthew:5 % 

```

When i try to run the script.

```
matthew-laptop:/home/matthew:5 % ~/bin/repo 
error: repo is not installed.  Use "repo init" to install it here.
matthew-laptop:/home/matthew:5 % 
```

So....

```
matthew-laptop:/home/matthew:5 % ~/bin/repo init
gpg: keyring `/home/matthew/.repoconfig/gnupg/secring.gpg' created
gpg: keyring `/home/matthew/.repoconfig/gnupg/pubring.gpg' created
gpg: /home/matthew/.repoconfig/gnupg/trustdb.gpg: trustdb created
gpg: key 920F5C65: public key "Repo Maintainer <repo@android.kernel.org>" imported
gpg: key 692B382C: public key "Conley Owens <cco3@android.com>" imported
gpg: Total number processed: 2
gpg:               imported: 2  (RSA: 1)

Get https://gerrit.googlesource.com/git-repo
remote: Counting objects: 117, done
remote: Finding sources: 100% (117/117)
remote: Total 2910 (delta 1533), reused 2910 (delta 1533)
Receiving objects: 100% (2910/2910), 2.46 MiB | 154.00 KiB/s, done.
Resolving deltas: 100% (1533/1533), done.
From https://gerrit.googlesource.com/git-repo
 * [new branch]      maint      -> origin/maint
 * [new branch]      master     -> origin/master
 * [new branch]      stable     -> origin/stable
<snip>
 * [new tag]         v1.9.4     -> v1.9.4
 * [new tag]         v1.9.5     -> v1.9.5
 * [new tag]         v1.9.6     -> v1.9.6
fatal: manifest url (-u) is required.
```

Needs a manifest url ?

Anyway, ~/bin is in my path. Make it the last item in your path as it's more secure and better from a security point of view.

```
matthew-laptop:/home/matthew:5 % echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home/matthew/bin
matthew-laptop:/home/matthew:5 % 

```

```
matthew-laptop:/home/matthew:5 % cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home/matthew/bin"
matthew-laptop:/home/matthew:5 %
``` 


That should get you nearer.

EDIT:

It creates these directories by the looks of it.

```
find . -maxdepth 1 -cmin -30
```

Kind regards

---


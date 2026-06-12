---
title: "Question on using pip to install python modules?"
date: 2016-09-27
forum: Programming Talk
---

### Post by CantankRus on 2016-09-27
I'm teaching myself python (only know simple bash) and have a question in regards to using pip.
Seems I can install modules using sudo...
eg
```
sudo pip install gkeyring 
```
where it warns:
> The directory '/home/glen/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. 
Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/home/glen/.cache/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. 
Check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
After installation I can use the command... 
```
gkeyring [COLOR="#808080"][options][/COLOR]
```

[SIZE=3]**or**[/SIZE]

I can install as a user...
```
pip install --user gkeyring
```
Then run by specifying the module ....
```
python -m gkeyring [COLOR="#808080"][options][/COLOR]

```
Should I use the -H flag if installing with sudo?
What's the benefit of user install over root?
What does "caching wheels" refer to?

---

### Post by Wadim_Korneev on 2016-10-18
[COLOR=#111111][FONT=Ubuntu]First, Python 2.7 is pre-installed on every currently supported Ubuntu release already. So you would not have had to install it first. That's why apt-get has told you that python is already in the newest version.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Second, you should usually prefer the Python modules packaged for apt from the repositories over those you get with pip from PyPI, unless you rely on the features or bug fixes of the latest version. The repository versions are often more or less outdated, but proofed to be compatible with whatever other package that is requiring them.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So to install pip for Python 2, run this:[/FONT][/COLOR]
```
sudo apt-get install python-pip

```[COLOR=#111111][FONT=Ubuntu]In case this old pip version is not working for your needs, you can later simply get the latest version (without uninstalling the old one!) using this command:[/FONT][/COLOR]
```
sudo -H pip install --upgrade pip

```[COLOR=#111111][FONT=Ubuntu]Another tip for you:
You should learn about and use virtualenvs, virtual python environments. You can install Python modules in a viertualenv only without affecting other virtualenvs or the system. It's the safest way to prevent version incompatibilities and messing around with packages needed by the system and other programs.[/FONT][/COLOR]

---

### Post by CantankRus on 2016-10-18
> **Wadim_Korneev said:**
> [COLOR=#111111][FONT=Ubuntu]First, Python 2.7 is pre-installed on every currently supported Ubuntu release already. So you would not have had to install it first. That's why apt-get has told you that python is already in the newest version.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Second, you should usually prefer the Python modules packaged for apt from the repositories over those you get with pip from PyPI, unless you rely on the features or bug fixes of the latest version. The repository versions are often more or less outdated, but proofed to be compatible with whatever other package that is requiring them.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So to install pip for Python 2, run this:[/FONT][/COLOR]

Thanks for the answer.
I understand this and only use repository versions.
python-pip was installed from the repos.
I used pip to install gkeyring which I use in a bash script.(Allows me to retrieve my password from gnomekeyring and type out with a mouse button press).
gkeyring isn't available from the repos.

The question was more about the different ways I can install a module if not available in the repo.
Should I install modules like this using **sudo -H**

---


---
title: "How does sudo work?"
date: 2006-01-09
forum: Programming Talk
---

### Post by harisund on 2006-01-09
Don't worry. I am not asking the standard sudo question. 

I just noticed one thing, if in a script titled "install" I have
sudo apt-get install $1 > packages

and I do ./install packagename (after chmod u+x install) it doesn't allow me to 

but if I simply have
apt-get install $1 > packages 

and I do sudo ./install packagename

it works? 

Is this how sudo works? I have authenticated myself with the NOPASSWD option in the sudoers file, and want to avoid typing sudo everytime (since not every time tab completion works and other stuff) and instead want the sudo to be in a script. I am not able to get that to work. 

However, if I call the script with sudo , it runs.. 

Anybody knows a way I can avoid sudo all together? 

Thanks !

---

### Post by tbrownaw on 2006-01-10
[QUOTE=harisund]sudo apt-get install $1 > packages[/QUOTE]
The redirect is executed as you. Since probably only root can write to packages, this won't work. Maybe try

sudo sh -c "apt-get install $1 > packages"

instead?

Tim

---

### Post by harisund on 2006-01-10
ah yes.. the redirect had some permission error since I was doing it outside my home folder.. thanks a lot really !

---


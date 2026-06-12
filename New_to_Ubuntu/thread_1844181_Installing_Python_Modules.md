---
title: "Installing Python Modules"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by phueaz on 2011-09-14
Hi all, 

I'm trying to install a python module for sympy. I've got an older version from the synaptic package manager. But the one I need is a more recent version. 

I've downloaded the most recent release and extracted the contents, I'm trying to use the Distutils install.

I was wondering how to use the following command correctly to make it install to the general python folder??? Not sure if that's the correct name. 

python setup.py install 

Allows me to use the modules if I launch from the downloaded and unpacked folder. But I want to be able to use it from anywhere. Ie
when I run 

import sympy 

I get the new version not the old one.

Thanks for any help

---

### Post by phueaz on 2011-09-14
So I've tried a few commands so its probably installed in lots of places. But the following command seems to have done the trick

sudo python setup.py install  --install-layout=deb

I tried a few like this 
sudo python setup.py install--home=~

Can anyone explain what the -- parts do and why the first one works. Would just like to know what I'm doing rather than trial and error.

Thanks

---


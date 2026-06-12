---
title: "I can't install this software"
date: 2019-08-07
forum: New to Ubuntu
---

### Post by hmdou on 2019-08-07
Hi,
I want to compile [COLOR=#ff0000]auto-multiple-choice_current_precomp.tar.gz[/COLOR] downloaded from [COLOR=#ff0000]auto-multiple-choice.net/download.fr[/COLOR] , when I extract the archive and execute the following commands in extraction directory : 
make all_precomp 
sudo make install
I get errors because in the description they said that you need these tools to compile :
    
[LIST]
[*]For building: libpoppler, libnetpbm 
[*]For use: perl-GTK, GraphicsMagick, LaTeX 
[/LIST]

please someone explain to me a detailed  explanation from installing tools to run this software
and thank you
PS: I know the installation of this software with the following command :
sudo add-apt-repository ppa:alexis.bienvenue/amc-stable && sudo apt-get update && sudo apt-get install auto-multiple-choice && sudo apt-get install msmtp

---

### Post by TheFu on 2019-08-07
Welcome to the forums.

I doubt anyone here is an expert on installing some random package off some random website. I've never heard of it before your port.

It is best to get detailed instructions from the project team who created it.
Tell them
* which version and OS you are running - the release numbers. lsb_release -a
* which of their install/readme files you are having problems following. What you find confusing.
* how far you got before getting confused (reference a line number in the file(s).
* any errors seen. Usually, the first error is all they want. Copy/paste the errors.

When providing this data, use commands, not explanations.  Show them proof, not an interpretation of what you believe.

---

### Post by Impavidus on 2019-08-07
I don't know about the software you're trying to install, but the requirements don't seem insurmountable.
> **hmdou said:**
> 
I get errors because in the description they said that you need these tools to compile :
    
[LIST]
[*]For building: libpoppler, libnetpbm 
[*]For use: perl-GTK, GraphicsMagick, LaTeX 
[/LIST]


For building you probably need the development versions of those packages. That's **libpoppler-dev** and **libnetpbm10-dev** or **libnetpbm9-dev**. I don't know if it needs one of those specifically or you can just choose.

I can't find a package named perl-GTK, but I can find **libgtk3-perl** and **libgtk2-perl**. Maybe you need one of those.

**graphicsmagick** is in the repositories too. You can install LaTeX with the package **texlive**, which will probably pull in enough dependencies to make this work.

You can install it all from the repositories. That's easy. If you install this software from a repository, all these dependencies would be handled automatically. That would be even easier, so this is the price you pay for installing from source. And the fact you don't get automatic updates.

---


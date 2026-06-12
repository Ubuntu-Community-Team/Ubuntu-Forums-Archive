---
title: "is there a way to integrate manually &quot;installed&quot; applications with synaptic?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-06-17
Hi folks, 

Case in point: Firefox and Sunbird. 

The way I'm running these two apps is I downloaded the tarballs (the latest version - Firefox RC3, Sunbird 0.8) from mozilla's web site, untarred the files into my /opt folder, and created application launchers in the menu to run those programs. 

Thing is, to run those programs I have to point to /opt/sunbird/sunbird and opt/firefox/firefox. Is there any way to use the commands "sunbird" and "firefox" (from terminal or otherwise) to run those programs?

I am assuming removal is simple - just delete the folders in /opt? I ask this because Firefox 3 (final version) comes out today (!!) - so firefox RC3 will have to go. 

Thanks, 

-'Mage

---

### Post by MasterSander on 2008-06-17
>  Package manager install: If you want to install it in a way that means it can be easily removed from inside the package manager, first install the package checkinstall. To install the package type sudo checkinstall. This will take slightly longer than a normal install and quite possibly you'll have to supply a description of the application yourself (and edit the other information slightly). If the need arises, this will be easy to take care of from inside the checkinstall program.  

Is that what you meant?

---

### Post by pedro_orange on 2008-06-17
I'm not sure about integrating it with Synaptic, but you can list all installed software by doing the following:

```
dpkg -l
```

Pipe it into less if you want a more managable view.
I would tend to remove packages by doing the following:

```
dpkg -r package-name
```

With regards to the launching from terminal. I think you could probably add a bash alias to serve that purpose.

---

### Post by UnWarierMage224 on 2008-06-17
Basically.

The thing is though, I don't think the firefox and sunbird tarballs from mozilla have checkinstall capabilities. I've tried that command and it doesn't work, unless I'm missing something?

-'Mage

---

### Post by MasterSander on 2008-06-17
You need to use the checkinstall when installing, now it's already too late to do that, but its andy for future purposes, you can use pedro_orange's advise to delete them and reinstall if needed (with or without checkinstall)

---

### Post by y-lee on 2008-06-17
> **UnWarierMage224 said:**
> The way I'm running these two apps is I downloaded the tarballs (the latest version - Firefox RC3, [noparse]Sunbird 0.8)[/noparse] from mozilla's web site, untarred the files into my /opt folder, and created application launchers in the menu to run those programs. 

Thing is, to run those programs I have to point to /opt/sunbird/sunbird and opt/firefox/firefox. Is there any way to use the commands "sunbird" and "firefox" (from terminal or otherwise) to run those programs?

You will need to add the directories **/opt/sunbird/** and **opt/firefox/** to your **$PATH**, read for instructions on doing that :[HOWTO: Add a Directory to my Path Statement/Variable]("http://www.newlinuxuser.com/howto-add-a-directory-to-my-path-statementvariable/") and [Re: Add directory to $PATH]("http://ubuntuforums.org/showpost.php?p=1020745&postcount=2").


> **UnWarierMage224 said:**
> I am assuming removal is simple - just delete the folders in /opt? I ask this because Firefox 3 (final version) comes out today (!!) - so firefox RC3 will have to go.


As far as I know that should work :)

---

### Post by N.N. on 2008-06-17
> **UnWarierMage224 said:**
> Thing is, to run those programs I have to point to /opt/sunbird/sunbird and opt/firefox/firefox. Is there any way to use the commands "sunbird" and "firefox" (from terminal or otherwise) to run those programs?

Yes. The shell has an environment variable called PATH that contains a list of directories to search through when you try to run a program. Thus when you type firefox in the terminal, the shell runs through its list of directories and checks each one for an executable file called firefox that it can run. This happens every time you run a program without specifying a full path to it.

The /usr/bin directory is included in the PATH list. It contains executable files for most of the programs you regularly use, or symbolic links to them. Thus in order to make the sunbird or firefox commands launch the applications in /opt/sunbird/sunbird and /opt/firefox/firefox, you must update the sunbird and firefox files in /usr/bin so that they point to the applications in /opt/sunbird/sunbird and /opt/firefox/firefox. This can be achieved by overwriting the existing sunbird and firefox files in /usr/bin with symbolic links pointing to the executables in /opt/sunbird/sunbird and /opt/firefox/firefox: ```
sudo ln -si /opt/sunbird/sunbird /usr/bin/sunbird
sudo ln -si /opt/firefox/firefox /usr/bin/firefox
```

> **UnWarierMage224 said:**
> I am assuming removal is simple - just delete the folders in /opt? I ask this because Firefox 3 (final version) comes out today (!!) - so firefox RC3 will have to go.

Yes, deleting the /opt/sunbird and /opt/firefox directories should do the trick. If you choose to reinstall the applications to another directory, however, remember to update the symbolic links in /usr/bin accordingly.

---

### Post by y-lee on 2008-06-17
> **N.N. said:**
> The /usr/bin directory is included in the PATH list. It contains executable files for most of the programs you regularly use, or symbolic links to them. Thus in order to make the sunbird or firefox commands launch the applications in /opt/sunbird/sunbird and /opt/firefox/firefox, you must update the sunbird and firefox files in /usr/bin so that they point to the applications in /opt/sunbird/sunbird and /opt/firefox/firefox. This can be achieved by overwriting the existing sunbird and firefox files in /usr/bin with symbolic links pointing to the executables in /opt/sunbird/sunbird and /opt/firefox/firefox: ```
sudo ln -si /opt/sunbird/sunbird /usr/bin/sunbird
sudo ln -si /opt/firefox/firefox /usr/bin/firefox
```




That will certainly work :)

---

### Post by UnWarierMage224 on 2008-06-17
OK so I tried following the steps at the "How to install anything in ubuntu site":

I CDed into the opt/sunbird directory, my terminal window looked like this:

```

USERNAME:/opt/sunbird$

```

I tried running the make command, got the following:

```

make: *** No targets specified and no makefile found.  Stop.

```

Tried running sudo checkinstall, was asked to input my sudo password, which I did, then the following came up:

```

sudo: checkinstall: command not found

```

I do have the build-essential package installed.

Next I tried running the sunbird command while within this directory, following error:

```

The program 'sunbird' is currently not installed.  You can install it by typing:
sudo apt-get install sunbird
bash: sunbird: command not found

```

Even though if you look inside the sunbird folder, there is a shell script "sunbird"...

-'Mage

---

### Post by y-lee on 2008-06-17
make checkinstall and that stuff only works if you are compilinga  program from source code which i don't think you are.

---

### Post by pedro_orange on 2008-06-17
I thought you already installed them?

```
dpkg -l | grep sunbird
```

---

### Post by N.N. on 2008-06-17
I believe the applications contained in the .tar.gz files you downloaded from mozilla's website are precompiled, hence trying to compile the contents of the archives with ./configure, make, and make install (or checkinstall) is unnecessary and won't work.

---

### Post by ibuclaw on 2008-06-17
For those who know their way around the deb package structure, could download the current firefox binaries from the repository, extract the contents and put the new firefox release in it's place.
After altering the various text files the contain the version numbers of the package, and re-compressing it back to a deb file.

Installing/Uninstalling (and integration with synaptic) should be easy as pie. :)

Regards
Iain

---


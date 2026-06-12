---
title: "Ubuntu Software Center Does Not Have APT Repositories Applications"
date: 2022-10-29
forum: New to Ubuntu
---

### Post by akhran2 on 2022-10-29
Greetings!

1) How do I search and install applications from APT repositories in Ubuntu Software Center? I searched for applications like "preload" and "apache" and they do not turn up in the search results. They are available on terminal "apt search" results.

2) I downloaded Google Chrome deb and installed it (double click on the file) through Ubuntu Software center installer. However, subsequently it does not appear in my Ubuntu Software search results. In this case, how do I uninstall it or update it through Ubuntu Software center?

Thank you in advance for your replies!

---

### Post by grahammechanical on 2022-10-29
The Chrome web browser is proprietary software. It is owned by Google, This means that the Ubuntu maintainers cannot audit the code to confirm that it does not contain malicious software. For this reason the Chrome web browser is not in the Ubuntu repositories and cannot be found in Ubuntu Software (store).

To install Chrome we either download and run a Chrome installer program or run certain commands in the terminal. This action puts a Google software repository in our list of software sources. To uninstall Chrome we run a certain command in the terminal.

Do not worry about Chrome getting updates. This will happen automatically when we run Software Updater or the update/upgrade commands in a terminal. I have just updated Ubuntu 20.04 and I received an update to Chrome web browser and it was not the first one I have received in the last few days.

If you open Software & Updates>Other Software tab you will see that there is an internet address to a Google repository. That is where updates to Chrome come from. This is nothing to do with the Ubuntu repositories.

Please read this web page. You will see instructions on how to install Chrome and how to uninstall it.

[https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu](https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu)

Such is the nature of Linux that we should not expect to find all Linux software in a distribution's software centre/store. Apache is another example. 

[https://ubuntu.com/server/docs/web-servers-apache](https://ubuntu.com/server/docs/web-servers-apache)

Preload is an example of software that could be useful and then again might make things worse.

[https://askubuntu.com/questions/110335/drawbacks-of-using-preload-why-isnt-it-included-by-default](https://askubuntu.com/questions/110335/drawbacks-of-using-preload-why-isnt-it-included-by-default)

Regards

---

### Post by akhran2 on 2022-10-29
It seems that Ubuntu Software Center only search/install/uninstall snap applications. 

For applications in APT repositories, I have to use apt related commands in the terminal to search/install/uninstall.

Is that correct?

Thank you for your reply!

---

### Post by Dennis N on 2022-10-30
Ubuntu Software is a subset of the Ubuntu Repositories and snap applications. If you don't see what you want, you resort to Synaptic or apt terminal.
In Ubuntu Software, Use the source box to see all the package types. Often the .deb is shown here. See the screenshot.

---

### Post by grahammechanical on 2022-10-30
> For applications in APT repositories, I have to use apt related commands in the terminal to search/install/uninstall.

There is no such thing as an APT repository. The man page for apt says this:

> apt provides a high-level commandline interface for the package management system. It is intended as an end user interface and enables some options better suited for interactive usage by default compared to more specialized APT tools like apt-get(8) and apt-cache(8). 

Ubuntu Software uses apt to install applications packaged in the Debian Package Management format (deb). Redhat has its own Redhat Package Management format (rpm) and Ubuntu Software will not offer rpm applications because they will not run on Debian based distributions such as Ubuntu. Ubuntu Software does not access Redhat repositories.

A lot of applications are packaged as snaps. Ubuntu Software offers them as a priority. There are still deb packaged applications in Ubuntu Software. In Ubuntu 20.04 there are two versions of Firefox. One as a snap and one as a deb. It is the same for Libreoffice.

I am of the opinion that over time the developers of major applications will publish their software as Flatpak, Snap or AppImage and not as deb or rpm or another kind of package management. Apparently these more modern package management formats are easier to do and give the developer greater control of the update/upgrade process. I am also of the opinion that the software stores of the various distributions will have to offer access to Flatpack, Snap and Appimage software repositories. It will be done for the convenience of their users.

Here is how to add Flatpack to Ubuntu Software.

[https://ubuntuhandbook.org/index.php/2020/06/install-flatpak-apps-software-ubuntu-20-04/](https://ubuntuhandbook.org/index.php/2020/06/install-flatpak-apps-software-ubuntu-20-04/)

At the moment it does not seem possible to have AppImage hub integrated into Ubuntu Software. We have to do things differently.

[https://ubuntuhandbook.org/index.php/2022/02/search-download-linux-apps-appimage/](https://ubuntuhandbook.org/index.php/2022/02/search-download-linux-apps-appimage/)

Regards

---

### Post by Holger_Gehrke on 2022-10-30
'gnome-software' - of which the Ubuntu Software Center is a reskinned and (in recent version of Ubuntu) snap-packaged variant - needs additional metadata for the presentation of the package in its front end. For a lot of the more technical / advanced packages this metadata (intentionally (?), to make it less likely a new user removes something important) does not exist, so these programs aren't shown in the Software Center. You can either use the apt-* family of tools on the command line or synaptic in the GUI to see these packages and install or remove them.

Holger

---

### Post by mIk3_08 on 2022-10-30
> **akhran2 said:**
> Greetings!
1) How do I search and install applications from APT repositories in Ubuntu Software Center? I searched for applications like "preload" and "apache" and they do not turn up in the search results. They are available on terminal "apt search" results.

I don't know what exactly is your point is. But in apt search results their are descriptions on packages you need. If you are about to install via apt you can just run the sudo and install commannd with the package name. 

> **akhran2 said:**
> how do I uninstall it or update it through Ubuntu Software center?
Thank you in advance for your replies!
In apt you can just run the update and upgrade command to run the update applications. And to uninstall just run the apt uninstall command of course with the administrative sudo command. Regards and cheers.

---


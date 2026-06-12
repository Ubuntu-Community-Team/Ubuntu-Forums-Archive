---
title: "HowTo: Easily Install Many Useful Programs Tools and Codecs"
date: 2006-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by motstudios on 2006-12-13
Greetings,

    This guide will hopefully be an easy to follow and easy to use guide to easily install many useful programs, tools, codecs and more using a simple script that will ask you yes or no questions and only install what you want.

Programs you CAN install with this guide:
* Lexmark z25-z35 Printer Drivers
* Java
* Flash
* Multimedia Codecs
* VLC Multimedia Player
* Tools needed to Compile source code (build-essential, checkinstall and alien)
* Firewall Manager (Firestarter)
* CD Burning Program (gnomebaker)
* HTML Editor (Quanta)
* StreamRipper
* StreamTuner
* FTP Client (GFTP)
* BitTorrent Client (BitTornado with GUI)
* XMMS Audio Player (XMMS, XMMS Skins and XMMS WMA Plugin)
* Kernel Sources (Kernel Sources along with programs needed to recompile Kernel)

Some Notes to Keep in mind:
* You WILL need internet access to complete this guide.
* This guide ONLY covers Ubuntu Dapper Xubuntu Dapper and Kubuntu Dapper.
* Edgy is NOT supported yet with this guide or script. It will be in the future.
* You have full control on what programs to install using this script.
* This script is released under GPL.
* This guide and script is supported to the best of my ability. All support requests should be sent to me via email at motstudios(AT)gmail.com
* This guide and the script will be updated as needed to include new useful programs. To request that a program be included, email me with your request and provide as much information about the program or programs you would like to see as possible.

Now on to the guide!

1. First off you will need to get a copy of the script, download the attached file to your home directory (/home/YOURUSERNAME/)

2. Once you get the tar.gz file downloaded, open a terminal (or konsole on Kubuntu). Please change YOURUSERNAME to your username. Issue the following command the terminal or konsole you just opened:

```
tar -xvzf /home/YOURUSERNAME/Ubuntu-Install-Script-Dapper-V2.tar.gz
```

This will extract the contents to:
/home/YOURUSERNAME/Ubuntu-Install-Script-Dapper-V2/

3. Issue this command in the same terminal or konsole. Remember to edit the YOURUSERNAME to your username.

```
cd /home/YOURUSERNAME/Ubuntu-Install-Script-Dapper-V2/
```

4. Issue the following command in the same terminal or konsole and answer the questions asked.

```
sudo sh ./Ubuntu-Install-Script-Dapper-V2.sh
```

5. Now your done! You can remove the Ubuntu-Install-Script-Dapper-V2 directory if you wish.

To uninstall any programs installed with this script, use the included package manager with Ubuntu to remove them. To remove the script, just delete the script directory.

Have fun and happy computing!
Mark

---


---
title: "Ruby on Rails + Radrails Ubuntu 9.10"
date: 2009-11-07
forum: Programming Talk
---

### Post by Stoneface on 2009-11-07
I installed Ubuntu 9.10 last week and decided to get into Ruby on Rails as well. Installed Apache, Ruby Module, Rails, all Ruby packages. As Radrails was recommended as IDE I donwloaded it. I needed Java Development Kit for this one so I downloaded that as well. But now I keep on starting up Radrails from the download folder by double clicking AptanaRadRails. 
How can I really give this program its proper place? And how can I make an Applications > Programming Radrails shortcut?

---

### Post by Stoneface on 2009-11-07
I think I will just install Eclipse + the Radrails plugin. Found a tip here: [http://howflow.com/tricks/install_rails_development_ide_aptana_radrails_on_ubuntu_8](http://howflow.com/tricks/install_rails_development_ide_aptana_radrails_on_ubuntu_8) . Eclipse I can download and install using apt-get. Will post results back later on.

---

### Post by Stoneface on 2009-11-08
Had problems / errors downloading all the latest plugins after I installed Eclipse via ```
sudo apt-get install eclipse
```. But today it seemed to work well again. But when I went to file > new there was no Rails option there. I wonder what plugin I missed after I updated pretty much everything?!

---

### Post by Stoneface on 2009-11-08
I am trying to use a ROR update link: [http://updatesite.rubypeople.org/release](http://updatesite.rubypeople.org/release) , but it seems to be pending forever. Maybe Radrails is the only Aptana solution out there that works with Ruby on Rails now?
PS Within Elclipse I found a download Ruby On Rails Get Plugin link but when I clicked that one I got:```
Network connection problems encountered during search.
  Unable to access "http://update.aptana.com/install/rails/3.2/".
    Unable to access site: "http://update.aptana.com/install/rails/3.2/" [Server returned HTTP response code: "403 Forbidden" for URL: http://update.aptana.com/install/rails/3.2/.]
    Server returned HTTP response code: "403 Forbidden" for URL: http://update.aptana.com/install/rails/3.2/.
    Unable to access site: "http://update.aptana.com/install/rails/3.2/" [Server returned HTTP response code: "403 Forbidden" for URL: http://update.aptana.com/install/rails/3.2/.]
    Server returned HTTP response code: "403 Forbidden" for URL: http://update.aptana.com/install/rails/3.2/.

```

---

### Post by Humbie on 2009-11-08
There is a detailed description of how to install the RadRails plugin in Eclipse [here]("http://www.radrails.org/radrails/plugin").

---

### Post by Stoneface on 2009-11-08
@ Humbie Thanks! Will check it out and let everyone now if it works out.

---

### Post by Stoneface on 2009-11-08
I used that link and then I got:
```
Cannot complete the install because of a conflicting dependency.
  Software being installed: Aptana RadRails 2.0.1.1257303250-79-17BFRYMUKSUR2NWA7RB8uWcFV (com.aptana.radrails.feature.feature.group 2.0.1.1257303250-79-17BFRYMUKSUR2NWA7RB8uWcFV)
  Software currently installed: Aptana Web Development Tools 1.2.7.024747 (com.aptana.ide.feature.feature.group 1.2.7.024747)
  Only one of the following can be installed at once: 
    Aptana Web Development Tools 2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc (com.aptana.ide.feature.feature.jar 2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc)
    Aptana Web Development Tools 1.2.7.024747 (com.aptana.ide.feature.feature.jar 1.2.7.024747)
  Cannot satisfy dependency:
    From: Aptana Web Development Tools 1.2.7.024747 (com.aptana.ide.feature.feature.group 1.2.7.024747)
    To: com.aptana.ide.feature.feature.jar [1.2.7.024747]
  Cannot satisfy dependency:
    From: Aptana Web Development Tools 2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc (com.aptana.ide.feature.feature.group 2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc)
    To: com.aptana.ide.feature.feature.jar [2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc]
  Cannot satisfy dependency:
    From: Aptana RadRails 2.0.1.1257303250-79-17BFRYMUKSUR2NWA7RB8uWcFV (com.aptana.radrails.feature.feature.group 2.0.1.1257303250-79-17BFRYMUKSUR2NWA7RB8uWcFV)
    To: com.aptana.ide.feature.feature.group [2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc]
```

I guess I will have to uninstall a package first..

---

### Post by Stoneface on 2009-11-08
Trying to uninstall the packages that cannot work with the Radrails plugin. Eclipse seems to be having a hard time though. Maybe I will shut it down and retry later. Will wait for a little while longer. ...

---

### Post by Stoneface on 2009-11-08
Well I think I managed to uninstall all that is needed. Now I am trying to install the Ruby on Rails or RadRails plugin. It is really slow again so I guess something is still off. If I would have known this would be so hard I would have tried an alternative programm / IDE.

------------------------ Edit -----------------------------------
Strike all that. Again an error:
```
Cannot complete the install because of a conflicting dependency.
  Software being installed: Aptana RadRails 2.0.1.1257303250-79-17BFRYMUKSUR2NWA7RB8uWcFV (com.aptana.radrails.feature.feature.group 2.0.1.1257303250-79-17BFRYMUKSUR2NWA7RB8uWcFV)
  Software currently installed: Aptana Web Development Tools 1.2.7.024747 (com.aptana.ide.feature.feature.group 1.2.7.024747)
  Only one of the following can be installed at once: 
    Aptana Web Development Tools 2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc (com.aptana.ide.feature.feature.jar 2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc)
    Aptana Web Development Tools 1.2.7.024747 (com.aptana.ide.feature.feature.jar 1.2.7.024747)
  Cannot satisfy dependency:
    From: Aptana Web Development Tools 1.2.7.024747 (com.aptana.ide.feature.feature.group 1.2.7.024747)
    To: com.aptana.ide.feature.feature.jar [1.2.7.024747]
  Cannot satisfy dependency:
    From: Aptana Web Development Tools 2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc (com.aptana.ide.feature.feature.group 2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc)
    To: com.aptana.ide.feature.feature.jar [2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc]
  Cannot satisfy dependency:
    From: Aptana RadRails 2.0.1.1257303250-79-17BFRYMUKSUR2NWA7RB8uWcFV (com.aptana.radrails.feature.feature.group 2.0.1.1257303250-79-17BFRYMUKSUR2NWA7RB8uWcFV)
    To: com.aptana.ide.feature.feature.group [2.0.1.1257296289-7D-17iOHMr0dIcmPqBAZc]
```

I guess the uninstallation did not work out. I seem to have two Aptana Development tools that cannot be there at the same time with RadRails

How can I completely remove eclipse and all its dependencies so I can start from scratch? I did a sudo apt-get automremove eclipse, but after a reinstallation I had the same sites in the available software site list?!!

---

### Post by Stoneface on 2009-11-10
Well I reinstalled Ubuntu on my Virtual Partition as VmWare Tools did no longer work properly. Then I installed Eclipse and Ruby SDK but then I got this error:```
An error occurred while installing the items
  session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Install, operand=null --> [R]org.eclipse.ant.ui 3.4.1.v20090901_r351, action=org.eclipse.equinox.internal.p2.touchpoint.eclipse.actions.InstallBundleAction).
The artifact file for osgi.bundle,org.eclipse.ant.ui,3.4.1.v20090901_r351 was not found.

```

I found a bug report here: [https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/477944](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/477944)

I am wondering if this is ever going to work out ...](*,)

---

### Post by Stoneface on 2009-11-10
Well after I read the bug report I mentioned earlier I installed several needed packages and then I could install the Ruby SDK plugin:
After installing all the other eclipse packages ```
sudo apt-get install eclipse-pde eclipse-jdt eclipse-platform
```

At restart it said Ruby was missing and if I wanted to install it. I said yes, but nothing seemed to happen. well, really close now :-)

---

### Post by Stoneface on 2009-11-10
Well I had to install Ruby on Rails and followed the guide @ [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails) . Ruby on Rails and Apache as well as MySQL have been installed. I only cannot figure out the configuration of the ruby module for Apache2 or mod passenger. I will work that out later
BTW, when I restarted Eclipse it located Ruby and asked for the installation of several plugins which I did. I will start working now on my first Ruby on Rails Projecte! :-)

---


---
title: "I have an issue in Ubuntu 21.10 with sudo apt-get update"
date: 2023-01-10
forum: New to Ubuntu
---

### Post by alexbaqua on 2023-01-10
Dear all,
I am trying to use "sudo apt-get update" from terminal in Ubuntu 21.10.When i use this command in terminal i am getting this error message that i wrote below. Before i make an attempt claiming some help for recovery.
I would be much appreciated.

```
Ign:1 http://archive.ubuntu.com/ubuntu impish InRelease        
Ign:2 http://archive.ubuntu.com/ubuntu impish-updates InRelease
Ign:3 http://archive.ubuntu.com/ubuntu impish-backports InRelease
Ign:4 http://archive.ubuntu.com/ubuntu impish-security InRelease
Err:5 http://archive.ubuntu.com/ubuntu impish Release
  404  Not Found [IP: 91.189.91.39 80]
Err:6 http://archive.ubuntu.com/ubuntu impish-updates Release
  404  Not Found [IP: 91.189.91.39 80]
Err:7 http://archive.ubuntu.com/ubuntu impish-backports Release
  404  Not Found [IP: 91.189.91.39 80]
Err:8 http://archive.ubuntu.com/ubuntu impish-security Release
  404  Not Found [IP: 91.189.91.39 80]
Hit:9 https://packages.microsoft.com/repos/edge stable InRelease
Reading package lists... Done            
E: The repository 'http://archive.ubuntu.com/ubuntu impish Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu impish-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu impish-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu impish-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by ne29914 on 2023-01-10
Your update server isn't working. Switch to a different server.

---

### Post by tea for one on 2023-01-10
Ubuntu 21.10 reached End of Life in July 2022.
It would be a good idea to back up your personal data, install a supported release i.e. 22.04 and restore your files.

---

### Post by deadflowr on 2023-01-10
> **tea for one said:**
> Ubuntu 21.10 reached End of Life in July 2022.
It would be a good idea to back up your personal data, install a supported release i.e. 22.04 and restore your files.

+1.
The update is trying to connect to a non-existent archive.
They have been removed. (well, moved really)

You can go about it the easy way or the hard way.
The easy way is what is quoted.
The hard way is this: [https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")
Backup your data regardless of method.

---

### Post by alexbaqua on 2023-01-11
This is my first year in Ubuntu things. Is this really end of Imprish or different server options that was updated somewhere else. Where is the system settings that are stored for update? I have just imagined that **/etc/apt/sources.list** carrying the list. Is that correct. Before making a gross change just claiming help from more professionals.
Regards

---

### Post by Impavidus on 2023-01-11
Ubuntu 21.10 was an interim release and as such only got 9 months of support, until July 2022. The final state of the repositories has been archived, but no more updates have been released in half a year. So it's really dead now. If you don't want a release upgrade twice a year, stick to the long term support releases: even.04. The current LTS release is 22.04. Older LTS releases still supported are 18.04 and 20.04, the next is planned to be 24.04.

As you're only one step behind the current LTS release, doing an EOL upgrade to that (link above) is fairly reliable, not really worse than if you did so before 21.10 died, although a bit harder. All settings will be kept for as far as they are still relevant. You can also install 22.04 over your 21.10 system without formatting, so you can keep your documents and selection of installed software, for as far as this is still available. In any case, make sure you've got backups of your documents, as sometimes things go wrong.

---

### Post by alexbaqua on 2023-01-11
Before making an installation for new Ubuntu version just installed the 22.10 on a flashdisk. Run the system without installation. Just tried sudo apt-get update command from terminal. But still this command is not working properly. I have to mention i am using this system out of region. Have no idea if server IP's are banned. Can you assist.
I would be much appreciated.

---

### Post by ne29914 on 2023-01-11
First, please stay with the LTS versions to begin with. Either 20.04 or 22.04.
Second, as your location is a total secret, it's impossible to say which server you should use.
Third, running an update on a live-boot thumb stick makes no sense at all.

---


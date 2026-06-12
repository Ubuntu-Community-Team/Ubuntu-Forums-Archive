---
title: "Multiple issues with &quot;sudo apt-get update&quot;"
date: 2017-04-08
forum: New to Ubuntu
---

### Post by tom167 on 2017-04-08
Hello. I have had this issue for awhile but didn't really think about it until today.
When I run the *apt-get update* command I get the following added to the end of it:
> W: GPG error: [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3
W: The repository 'https://repo.skype.com/deb stable InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

This is a new installation of Ubuntu with xenial packages only installed. I have applications it mentions such as ffmpeg and skype for linux beta, but I don't know what could have caused these errors.
I have installed skype for linux using a .deb file and ffmpeg said it was an xenial repository.
I am using Ubuntu 16.04. Please, how can I solve this issue?

---

### Post by RobGoss on 2017-04-08
Hello and welcome to the forum, There are PPA's that need to be removed from your list 

Open up **Software & updates**, click on **Other software**, the first one I see that need to removed is as follow
```
E: Failed to fetch http://ppa.launchpad.net/kirillshkro...amd64/Packages 404 Not Found
```

```
W: GPG error: https://repo.skype.com/deb stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3
```

```
W: The repository 'https://repo.skype.com/deb stable InRelease' is not signed
```

Uncheck and remove the ones listed above from your system

Then just update your system and reboot
```
sudo apt-get update
```


If you look closely when receiving these error messages from your system it is telling you what applications are giving you problems, it looks like **Skype** is the culprit in this case along with a **PPA** that is no longer available, so you might have to find an alternative way of installing **Skype**

---

### Post by howefield on 2017-04-09
For the first error (skype) you could try..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 1F3045A5DF7587C3
```

For the second error you will have to remove the ffmpeg PPA that you added as there is no xenial repository available for that PPA, either by the method above or removing the relevant file from your /etc/apt/source.list.d/ folder.

Basically you are querying a non existent source. Going to the URL in your error will show you what is available....[http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/](http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/)

---

### Post by tom167 on 2017-04-09
Thank you both for your help.
I appreciate it.

---


---
title: "The list of sources could not be read. Help"
date: 2021-01-30
forum: New to Ubuntu
---

### Post by pockl on 2021-01-30
I am an Ubuntu noob. I type sudo apt-get update and i get this error. 

```
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/spotify.list
E: The list of sources could not be read.
```

why is it in spotify and how do i make my stuff work? probably a super easy fix

---

### Post by deadflowr on 2021-01-30
You have a mistake in the file  /etc/apt/sources.list.d/spotify.list
You need to edit that file and remove whatever the issue related to sudo is.
If you're not sure about what needs to be fixed post the contents of the file 
```
cat /etc/apt/sources.list.d/spotify.list
```
then copy the output and paste it into this thread.

---

### Post by ActionParsnip on 2021-01-30
Sounds like you tired to edit the file manually.
If you run
```

sudo rm /etc/apt/sources.list.d/spotify.list
curl -sS https://download.spotify.com/debian/pubkey_0D811D58.gpg | sudo apt-key add - 

echo "deb http://repository.spotify.com stable non-free" | sudo tee /etc/apt/sources.list.d/spotify.list

``` 

Then you can install the Spotify client:

```
 
sudo apt-get update && sudo apt-get install spotify-client
 
``` 

https://www.spotify.com/us/download/linux/

---


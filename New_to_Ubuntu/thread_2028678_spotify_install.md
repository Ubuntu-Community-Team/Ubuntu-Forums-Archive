---
title: "spotify install"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by nhyrum on 2012-07-18
how do i install spotify? going to the site they say to type in some mumbo jumbo tha i dont understand. i have it already runing under wine but the sound doesnt work. i actually think my sound doesnt work at all. i have never had the problem of my sound noot working at all. ive tried the sound tester, but still nothing works, not even with good headphones in.

so essentially two questions.
1 how do i either fix spotify running under wine or install it for ubuntu, and
2how do i fix my sound? some updates are being installed and maybe thats why

---

### Post by Daveth on 2012-07-18
this is 1 way
[http://www.liberiangeek.net/2012/04/the-quickest-way-to-install-spotify-client-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/the-quickest-way-to-install-spotify-client-in-ubuntu-12-04-precise-pangolin/)

but is the linux client version which is only enabled for Spotify Premium subscribers; the "free" use version should run under WINE but by clicking the windows .exe file, though I haven't fired mine up since loading up Precise.

Do you not get any sound at all, not even with media players etc??

---

### Post by brainwash on 2012-07-18
The Linux preview version works for Premium _and_ Free users. It's quite stable and runs smooth. If you need further information or help, simply visit the [Linux subsection]("http://community.spotify.com/t5/Desktop-Linux/bd-p/spotifylinux") of the Spotify Community forum.

**Installation (unofficial repository):**
```
echo "deb http://repository.spotify.com stable non-free" | sudo tee /etc/apt/sources.list.d/spotify.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
sudo apt-get update
sudo apt-get install spotify-client
```

---


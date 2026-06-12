---
title: "Help with cah clone in docker"
date: 2020-04-24
forum: New to Ubuntu
---

### Post by ptmuldoon on 2020-04-24
I have been trying for the last 2 days in getting a cah clone I came across on github to work.  The creator of the game has been helpful in getting me started, but I think perhaps it may not be the game giving me issues anymore, but perhaps my ubuntu server setup.

The cah came I am trying to get going can be found here: [https://github.com/olback/cah](https://github.com/olback/cah)

The readme docs do not mention it, but the creator was able to help me by letting me know that after cloning, you do need to run both the /scripts/setup.sh and /scripts/angular.sh files.

The issue I am having is that the game will load on port 5000 like it says, but I do not get any cards to use in the game (like you can see on the creators site)

When the dockers are created, it creates 2 dockers, one of which is a postgres docker.  And I was able to connect to the postgres docker and learn that the database and tables are created for the game.

What I think (just guessing) is that maybe the game is not able to connect to the postgres docker?  When I have tried to run the /scripts/postgres/install.sh separately, I get a Peer authentication error.

My main testing steps/setup is.

1. Fresh Ubuntu 19 Server install (as VM inside Proxmox, setup a VM and not a container)
2. update packages, install nodejs, docker, docker-compose, npm (I have been installing nodejs 13.13)
3. installed angular.js  
4. git clone and then run the scripts.

I get a few warnings here and there, but things seem to install properly.

Yet when accessing the game, I get no cards.

Again, my only guess is something with postgresql and permissions, but I have idea if it is my setup or something else.

If anyone is willing to give a try, I would be very grateful as I am working to try and provide a little laughter to family and friends in these difficult lock down times.

Thank you
PT

---


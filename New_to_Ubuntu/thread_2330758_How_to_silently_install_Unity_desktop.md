---
title: "How to silently install Unity desktop?"
date: 2016-07-14
forum: New to Ubuntu
---

### Post by adamhems on 2016-07-14
I am trying to create a Dockerfile that auto-installs .NET and Visual Studio Code, which requires a desktop, on Ubuntu 16.04. I can get everything to build and run except for the last line of my Dockerfile:
```
apt-get install -y ubuntu-desktop
```
This line fails for me as it hangs - it waits for input from the user (selecting a keyboard). *Is there a way to pass some values to this command so that it silently completes?*
Here is my complete Dockerfile:

```
FROM ubuntu:16.04
RUN apt-get update && apt-get install -y --no-install-recommends unzip libgtk2.0-0 libgconf-2-4 libnss3 libasound2 libxtst6
RUN apt-get -y upgrade
RUN apt-get -f install -y libnotify4
RUN apt-get -y install npm
RUN apt-get -y install apt-transport-https
RUN npm install azure-cli -g
RUN ln -s /usr/bin/nodejs /usr/bin/node
RUN sh -c 'echo "deb [arch=amd64] [https://apt-mo.trafficmanager.net/repos/dotnet/](https://apt-mo.trafficmanager.net/repos/dotnet/) xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
RUN apt-key adv --keyserver apt-mo.trafficmanager.net --recv-keys 417A0893
RUN apt-get upgrade
RUN apt-get -y update
RUN apt-get install -y dotnet-dev-1.0.0-preview2-003121
ADD [https://go.microsoft.com/fwlink/?LinkID=760868](https://go.microsoft.com/fwlink/?LinkID=760868) vscode-amd64.deb
RUN dpkg -i vscode-amd64.deb
ADD [http://download.nomachine.com/download/5.1/Linux/nomachine_5.1.26_1_amd64.deb](http://download.nomachine.com/download/5.1/Linux/nomachine_5.1.26_1_amd64.deb) nomachine_5.1.26_1_amd64.deb
RUN dpkg -i nomachine_5.1.26_1_amd64.deb
RUN apt-get install -y ubuntu-desktop
```


I am using automation to build and automatically deploy the latest versions of the various components I need to the public cloud (Azure) and everything works except for the desktop install. Any pointers or guidance gratefully received!!

---


---
title: "License not working inside snap package"
date: 2019-11-12
forum: New to Ubuntu
---

### Post by manoj-prabhakar on 2019-11-12
we're using **ubuntu 16.04** for our packaging of java application in **snap**.  we’ve developed a Java application for face recognition with the help  of third party SDK. The application needs license from the third party  SDK to run. The license should be running as a separate instance in the  installed machine.

  After packaging of our application along with the dependencies and  licenses using snap, Our Java application is not detecting the running  license instance.

  The License file will be run through the shell script which is provided by the SDK, will be running locally on port **5000**.

  Should we have to follow any other steps while packaging the application particularly for this type of licensing?

  I've attached my snapcraft.yaml file below

```


name: facecheck # you probably want to 'snapcraft register <name>'
base: core18 # the base snap is the execution environment for this snap
version: '1.0' # just for humans, typically '1.2+git' or '1.3.2'
summary: Face recognition # 79 char long summary
description: |
  This application is used to recognise and detect the persons face
  with the enrolled data from database.

grade: devel # must be 'stable' to release into candidate/stable channels
confinement: devmode # use 'strict' once you have the right plugs and slots

apps:
 facecheck:
   command: usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java -jar $SNAP/Bin/Java/simple-surveillance-application.jar
   environment:
     JAVA_HOME: $SNAP/usr/lib/jvm/java-1.8.0-openjdk-amd64
     PATH: $JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
     LD_LIBRARY_PATH: $SNAP/Lib/Linux_x86_64
   plugs: [desktop, home, camera, x11, desktop-legacy, opengl, alsa, pulseaudio, network-bind]
   autostart: Facecheck-surveillance.desktop

parts:
  facecheck:
   source: .
   plugin: dump
   build-packages: 
     - nvidia-384-dev
     - libgtk-3-dev
     - gstreamer1.0-vaapi
     - vainfo
     - openjdk-8-jre
     - openjdk-8-demo
     - libgdk-pixbuf2.0-dev
     - alsa-utils
     - libasound2-data
     - libasound2-plugins
     - libasound2
     - libopus-dev
     - libortp-dev
     - gcc
     - g++
     - make
     - libgudev-1.0-0
     - libgudev-1.0-dev 
     - libgstreamer1.0-0 
     - gstreamer1.0-plugins-base 
     - gstreamer1.0-plugins-good 
     - gstreamer1.0-plugins-bad 
     - gstreamer1.0-plugins-ugly 
     - gstreamer1.0-libav 
     - gstreamer1.0-doc 
     - gstreamer1.0-tools 
     - gstreamer1.0-x 
     - gstreamer1.0-alsa 
     - gstreamer1.0-gl 
     - gstreamer1.0-gtk3 
     - gstreamer1.0-qt5 
     - gstreamer1.0-pulseaudio
     - libfontconfig1-dev 
     - libfreetype6-dev 
     - libpng-dev
     - libcairo2-dev 
     - libjpeg-dev 
     - libgif-dev
     - libgstreamer-plugins-base1.0-dev
     - python-gst-1.0 
     - python3-gst-1.0
     - postgresql
     - postgresql-contrib
     - odbc-postgresql
     - unixodbc
     - unixodbc-dev
     - build-essential
     - manpages-dev
   stage-packages:
     - libgpm2
     - libslang2 
     - libnvidia-compute-390
     - openjdk-8-jre
     - openjdk-8-demo
     - nvidia-384-dev
     - libgtk-3-dev
     - gstreamer1.0-vaapi
     - vainfo
     - libgdk-pixbuf2.0-dev
     - alsa-utils
     - libasound2-data
     - libasound2
     - libasound2-plugins
     - gcc
     - g++
     - make
     - libgudev-1.0-0
     - libgudev-1.0-dev
     - libgstreamer1.0-0 
     - gstreamer1.0-plugins-base 
     - gstreamer1.0-plugins-good 
     - gstreamer1.0-plugins-bad 
     - gstreamer1.0-plugins-ugly 
     - gstreamer1.0-libav 
     - gstreamer1.0-doc 
     - gstreamer1.0-tools 
     - gstreamer1.0-x 
     - gstreamer1.0-alsa 
     - gstreamer1.0-gl 
     - gstreamer1.0-gtk3 
     - gstreamer1.0-qt5 
     - gstreamer1.0-pulseaudio
     - libfontconfig1-dev 
     - libfreetype6-dev 
     - libpng-dev
     - libcairo2-dev 
     - libjpeg-dev 
     - libgif-dev
     - libgstreamer-plugins-base1.0-dev
     - python-gst-1.0 
     - python3-gst-1.0
     - postgresql
     - postgresql-contrib
     - odbc-postgresql
     - unixodbc
     - unixodbc-dev
     - build-essential
     - manpages-dev

```

---

### Post by Frogs Hair on 2019-11-12
Hello and Welcome

Since you have developed a snap application the following forum may be a better place for assistance.

[https://forum.snapcraft.io/categories](https://forum.snapcraft.io/categories)

---


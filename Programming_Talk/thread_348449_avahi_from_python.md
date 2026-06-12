---
title: "avahi from python"
date: 2007-01-28
forum: Programming Talk
---

### Post by ssam on 2007-01-28
i am trying to make a remote control type system, with a client and server that run on two computers. the server has a list of actions (eg play/pause music, next song etc), which it sends to the client. the client displays buttons for each action. i am using python

currently the server can read a list of actions from an xml file (they can by shell commands or dbus actions). the client can retrieve the list of actions (and their names) over xmlrpc, and draws the buttons. clicking the buttons sends a message back to the server, and they are executed.

the trouble is that at the moment the ip address of the server is hardcoded into the client. rather than making the user have to type in an ip address, i'd like to avahi. this should let the server advertise itself to the network, and the client find it and connect.

unfortunately i can't find any simple examples of how to do this. all the avahi examples require setting up call back functions to handle discovering services, and are as long as the rest of my code is so far.

is there a simple way to advertise a service and then find it? otherwise i am considering wrapping something around the avahi-publish and avahi-browse command line apps.

---


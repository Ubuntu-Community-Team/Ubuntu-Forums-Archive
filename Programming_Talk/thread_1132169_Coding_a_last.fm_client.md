---
title: "Coding a last.fm client"
date: 2009-04-21
forum: Programming Talk
---

### Post by Metallion on 2009-04-21
I was just wondering if anyone has experience with this? I've recently fallen in love with last.fm and another love of mine is the Nintendo DS. I've been looking around for a homebrew DS last.fm client but it doesn't seem to exist yet.

I see some open source apps like Amarok that support last.fm so it must be possible to code a client and I might be interested in doing this for the DS if I find the time.

Is there anyone around that has any experience with this and if so, could you give me an idea about how hard it is?

Thanks

---

### Post by Yacoby on 2009-04-21
> **Metallion said:**
> I was just wondering if anyone has experience with this? I've recently fallen in love with last.fm and another love of mine is the Nintendo DS. I've been looking around for a homebrew DS last.fm client but it doesn't seem to exist yet.

I see some open source apps like Amarok that support last.fm so it must be possible to code a client and I might be interested in doing this for the DS if I find the time.

Is there anyone around that has any experience with this and if so, could you give me an idea about how hard it is?

Thanks

I found it really easy. I found all the info on google. It was a couple of get requests to login and start a radio. It then provided a list of temporary links formed as XML to the mp3 files.

Their official client is opensource, so you could always take a look at that if you were stuck.

---

### Post by MadCow108 on 2009-04-21
This might help:
[http://code.google.com/p/thelastripper/wiki/LastFM12UnofficialDocumentation](http://code.google.com/p/thelastripper/wiki/LastFM12UnofficialDocumentation)

but I don't know if it's up to date.

---

### Post by days_of_ruin on 2009-04-21
Good luck:D
I would love to be able to use last.fm on my ds.:D

---

### Post by Yacoby on 2009-04-21
> **MadCow108 said:**
> This might help:
[http://code.google.com/p/thelastripper/wiki/LastFM12UnofficialDocumentation](http://code.google.com/p/thelastripper/wiki/LastFM12UnofficialDocumentation)

but I don't know if it's up to date.

Yup, that is the info I used. And my program still works :D

---

### Post by Metallion on 2009-04-22
thanks guys! That page looks like some great reference. I see on the last.fm API page that can ask for a API account. Did you do this for your app, Yacoby? I'd prefer if I could experiment a bit without opening an account first. I plan to familiarize myself with the API through some simple test apps on computer my before I start putting the thing on the DS.

Also is the app you wrote open source? If so, could I download it somewhere? Since it's built using MadCow's documentation page, it could be some great extra reference.

---

### Post by Yacoby on 2009-04-22
> 
see on the last.fm API page that can ask for a API account. Did you do this for your app, Yacoby? I'd prefer if I could experiment a bit without opening an account first. I plan to familiarize myself with the API through some simple test apps on computer my before I start putting the thing on the DS.
I didn't do anything with the offical API, as I was only interested in the track data, not in interacting with anything else of their services.

> Also is the app you wrote open source? If so, could I download it somewhere? Since it's built using MadCow's documentation page, it could be some great extra reference.It isn't available anywhere due to it not working flawlessly. (Other bits of the app, not the last.fm bit) and also it not being legal in many countries.

The main bits of code I have dealing with last.fm are here

[PHP]
#example
hand = lastfm.Handshake()

hand.shake(ini.general["username"], md5.new(ini.general["password"]).hexdigest(), "en", "win32")

#define the station
station = lastfm.Station(hand, ini.general["lang"])
station.playSimalar(ini.general["artistslike"].replace(" ", "+"))


playlist = lastfm.Playlist(hand)
playlist.download()

tracks = playlist.getPlaylist()
for t in tracks:
    print(t.location)[/PHP]

[PHP]#Copyright (c) 2009 Jacob Essex

#Permission is hereby granted, free of charge, to any person
#obtaining a copy of this software and associated documentation
#files (the "Software"), to deal in the Software without
#restriction, including without limitation the rights to use,
#copy, modify, merge, publish, distribute, sublicense, and/or sell
#copies of the Software, and to permit persons to whom the
#Software is furnished to do so, subject to the following
#conditions:

#The above copyright notice and this permission notice shall be
#included in all copies or substantial portions of the Software.

#THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
#EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
#OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
#NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
#HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
#WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
#FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
#OTHER DEALINGS IN THE SOFTWARE.


import urllib, md5

###############################################
#Handshake
###############################################


#EXAMPLE RET
#    session=ae1eb54a11615e605d61d6e83dde71bc
#    stream_url=http://87.117.229.85:80/last.mp3?Session=ae1eb54a11615e605d61d6e83dde71bc
#    subscriber=0
#    framehack=0
#    base_url=ws.audioscrobbler.com
#    base_path=/radio
#    info_message=
#    fingerprint_upload_url=http://ws.audioscrobbler.com/fingerprint/upload.php

#NOTES
#    * session: The session ID for the current session. This is what associates the Last.FM username with the IP address of the device on the AudioScrobbler system.
#    * stream_url (depreciated): The URL of the Last.FM ShoutCast/MP3 stream. Beginning version 1.2, this is no longer current. Refer to section "Request Playlist."
#    * subscriber: Indicates if the user submitted to handshake.php is a subscriber. kv: "0" (not a subscriber), "1" (a subscriber).
#    * framehack: Unknown.
#    * base_url: The address to which all future HTTP posts should be sent. See base_path.
#    * base_path: The root path, as related to the base_url, to which all future HTTP posts should be sent (e.g. the functions for playing and controlling the stream). See base_url.
#    * info_message: Unknown. Most likely a vehicle to send messages to the client.
#    * fingerprint_upload_url: Post URL for Last.fm fingerprinting system. 



class Handshake:
    def __init__(self):
        self.sessionID = 0
        self.isSubscriber = 0
        self.baseUrl = ""
        self.basePath = ""
        self.infoMessage = ""
        self.fingerprintUploadUrl = ""

    def shake(self, usr, md5pass, lang, platform):
        url = "http://ws.audioscrobbler.com/radio/handshake.php?version=1.3.1.1&platform="
        url += platform + "&username="+usr+"&passwordmd5="+md5pass+"&language="+lang

        f = urllib.urlopen(url)
        s = f.read()
        f.close()

        #devide up
        lines = s.split("\n") #i assume \n?

        #get the data we need.
        for l in lines:
            if l.find("session") == 0:
                 self.sessionID = l.replace("session=", "")
            if l.find("base_url") == 0:
                self.baseUrl = l.replace("base_url=", "")
            if l.find("base_path") == 0:
                self.basePath = l.replace("base_path=", "")

               
###############################################
#Station
###############################################

#Request
#
#Example:
#
#   http://[base_url][base_path]/adjust.php?session=[sessionID]&url=[LASTFMURI]&lang=[LANGUAGE]
#
#Post Variables:
#
#    * base_url: Given as part of the response to Handshake.php; explicitly "base_url".
#    * base_path: Given as part of the response to Handshake.php; explicitly "base_path".
#    * sessionID: Given as part of the response to Handshake.php; explicitly "session".
#    * url: The Last.FM URI for which you want to tune in. Refer to Appendix A for more info.
#    * lang: Value is equal to an ISO 639.1 language code. kv: "en" (English), "de" (German). 

class Station:
    def __init__(self, lang):
        self.baseUrl = ""
        self.basePath = ""
        self.sessionID = 0
        self.lang = lang

    def __init__(self, hand, lang):
        self.baseUrl = hand.baseUrl
        self.basePath = hand.basePath
        self.sessionID = hand.sessionID
        self.lang = lang

    def setData(self, base, path, session, lang):
        self.baseUrl = base
        self.basePath = path
        self.sessionID = session
        self.lang = lang


    def playSimalar(self, artist):
        return self._play("lastfm://artist/"+artist+"/similarartists")

    def playNeighbours(self, usr):
        return self._play("lastfm://user/"+usr+"/neighbours")


    def _play(self, url):
        #get the rul requrested
        url = "http://"+self.baseUrl+self.basePath+"/adjust.php?session="+self.sessionID+"&url="+url+"&lang="+self.lang
        f = urllib.urlopen(url)
        s = f.read()
        f.close()

        #see if it failed or not. A good response is:
        
        #response=OK
        #url=lastfm://user/Yacoby/neighbours
        #stationname=Meine Nachbarn
        #discovery=true
        
        lines = s.split("\n")
        for l in lines:
            if l.find("response") == 0:
                if l.replace("response=", "") == "OK":
                    return True
                else:
                    return False

        #something bad happened
        return False


###############################################
#Track
###############################################
#storage class for holding track data
    
class Track:
    def __init__(self):
        self.title = ""
        self.album = ""
        self.creator = ""
        self.location = ""
        self.duration = 0

###############################################
#Playlist
###############################################

import xml.dom.minidom
from xml.dom.minidom import Node

    
class Playlist:
    def __init__(self, hand):
        self.baseUrl = hand.baseUrl
        self.basePath = hand.basePath
        self.sessionID = hand.sessionID

        self.playListXML = ""

        self.playList = []

    def download(self):
        url = "http://"+self.baseUrl+self.basePath+"/xspf.php?sk="+self.sessionID+"&discovery=0&desktop=1.3.1.1"
        f = urllib.urlopen(url)
        self.playListXML = f.read()
        f.close()

        self._parse()

    def _getText(self, elem):
        for node1 in elem:
                for node2 in node1.childNodes:
                    if node2.nodeType == Node.TEXT_NODE:
                        return node2.data

    def _parse(self):
        doc = xml.dom.minidom.parseString(self.playListXML)
        for node in doc.getElementsByTagName("track"):

            t = Track()
            t.title = self._getText(node.getElementsByTagName("title"))
            t.album = self._getText(node.getElementsByTagName("album"))
            t.creator = self._getText(node.getElementsByTagName("creator"))
            t.location = self._getText(node.getElementsByTagName("location"))
            t.duration = self._getText(node.getElementsByTagName("duration"))
            self.playList.append(t)

    def getPlaylist(self):
        return self.playList
[/PHP]

---


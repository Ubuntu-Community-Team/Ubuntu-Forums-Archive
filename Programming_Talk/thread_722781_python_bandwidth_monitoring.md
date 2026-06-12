---
title: "python bandwidth monitoring"
date: 2008-03-12
forum: Programming Talk
---

### Post by themusicwave on 2008-03-12
Hey everyone,

I'd like to write a simple script to monitor bandwidth.  I would like to do it in Python.  I have done some searching and haven't turned up much.  I have also never really done any socket programming in python, but I have in Java and C++.

Basically, I want to monitor the incoming and out going Kb/s

Any ideas?  Perhaps some linux command I could hook into and parse the output of?

Thanks,

Jon

---

### Post by ghostdog74 on 2008-03-12
in *nix, you can use ntop. If you want to code your own using Python, googling for "Python network monitoring" might bring you some hits

---

### Post by themusicwave on 2008-03-12
Thanks I'll give ntop a try.  I am only concerned with *nix for now.

I appreciate the suggestion.

---

### Post by pmasiar on 2008-03-12
links/guides like: 
[http://docs.python.org/lib/module-socket.html](http://docs.python.org/lib/module-socket.html) (docs - of course you checked that :-) )
[http://www.amk.ca/python/howto/sockets/](http://www.amk.ca/python/howto/sockets/) (AMK is known expert)
Examples: 
[http://www.example-code.com/python/pythonsocket.asp](http://www.example-code.com/python/pythonsocket.asp)
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52218](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52218) - ActiveState CookBook is well-known code samples repository, reviewed by experts

more from ASPN: [http://www.google.com/search?q=python+socket+recipe+site%3Aactivestate.com](http://www.google.com/search?q=python+socket+recipe+site%3Aactivestate.com)

---

### Post by themusicwave on 2008-03-13
I did look at the docs last night and had some ideas.

I'll check out your other links tonight.  Thanks for the suggestions!

Also, just to clarify what exactly I am trying to do, here is my little project.

I am essentially trying to save myself some energy(and computer lifetime) by writing a program to shutdown my computer on various events.

So far it can do it on a timer and on a process.  Essentially I can say "computer when process X finishes turn yourself off. 

Now what I want to do is say "Computer when the downloads all finish turn off"
 
I hope to do this by monitoring the bandwidth and seeing when it gets to around 0 and stays that way for a minute.  That way it won't matter whether it is a bit torrent, browser based download, FTP or whatever.

So thats why I need a way to hook into the bandwidth monitoring.  I often do large downloads and long running processes over night.  Sometimes they finish halfway through the night, but I don't get out of bed to check.  So the computer sits on half a night wasting power.

The program is coming along ok, I have most of the back end done, with the exception of the bandwidth monitor.

Thanks for all the suggestions,

Jon

---

### Post by nanotube on 2008-03-13
> **themusicwave said:**
> 
So thats why I need a way to hook into the bandwidth monitoring.  I often do large downloads and long running processes over night.  Sometimes they finish halfway through the night, but I don't get out of bed to check.  So the computer sits on half a night wasting power.


an even better solution to computer wasting power: just install folding@home (and join [teamubuntu]("https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu") of course), and have it do usefull processing with all that idle cpu time while it sits around at night. :) that way, even if your dl finishes early, your comp is still doing useful work. :)

---

### Post by imdano on 2008-03-13
You might consider monitoring /proc/net/dev, which prints out packet info for all your network interfaces.

---

### Post by themusicwave on 2008-03-13
> **imdano said:**
> You might consider monitoring /proc/net/dev, which prints out packet info for all your network interfaces.


That was exactly what I needed!  I think I got it, it appears to be within 1 Kb/s of the system monitor and that could be just due to timing of my update vs their update.

Thanks for the great suggestion!

---

### Post by themusicwave on 2008-03-13
Here is the code for those curious and those who stumble upon this thread in the future.

Suggestios welcome, this certainly isn't a final version.  I am also still learning python, so bear with me.

Basically this class encapsulates a monitor for an interface.  You can cal it's update method to update it's state.  Output just makes it print a dump of this state.

Future enhancements I'd like to see mainly including thread this so it updates itself every second.

Like I said, not perfect, but a definite proof of concept.

[PHP]
#ConnectionMonitor
#Author: Jon Parise jlparise@gmail.com
#Date: 3/13/2008
#Description:  Montiors the specified interface and stores it's current state.  This includes read/write bytes, bytes per second 
#and other information.


import time

class ConnectionMonitor():
    
    def __init__(self,name):
        """Construct it based on a name like eth1, it will monitor that name"""
        self.__netFile = open("/proc/net/dev",'r')
        
        self.__name = name
        self.__lastCheckTime = time.time()
        self.__timeDiff = 0
        
        self.__lastReadBytes = 0
        self.readBytes = 0
        self.readPackets = 0
        self.readErrs = 0
        self.readDrop = 0
        self.reafFifo = 0
        self.readFrames = 0
        self.readCompressed = 0
        self.readMulticast = 0  
        self.readBps = 0
        #parse write info
        self.__lastWriteBytes =0
        self.writeBytes = 0
        self.writePackets = 0
        self.writeErrs = 0
        self.writeDrop = 0
        self.writeFifo = 0
        self.writeFrames = 0
        self.writeCompressed = 0
        self.writeMulticast = 0   
        self.writeBps =0
        #self.update()
    
    """
    Update
    
    Inputs - self - reference to this class instance
    
    Description: Updates the state of the interface and calculates Bytes per second
    """
    def update(self):
        self.__netFile = open("/proc/net/dev",'r')
        line =" "
        found = False
        #read all the lines till the right one is found
        while not line == None and not found:
            line = self.__netFile.readline()
            #find only the line with this name
            if line.find(self.__name) > 0:
                self.__netLine = line
                found = True
                
        if(found):
            tempSplit = line.split(" ")
            
            netSplit = []
            for item in tempSplit:
                if len(item) >0:
                    netSplit.append(item)

            #update times
            prevTime = self.__lastCheckTime
            currTime = time.time()
            
            self.__timeDiff = currTime - prevTime
            
            self.__lastCheckTime = currTime
            #update last read/write bytes
            self.__lastReadBytes = self.readBytes
            self.__lastWriteBytes = self.writeBytes
            
            #parse read info
            self.readBytes = int(netSplit[0].lstrip(self.__name + ":"))
            self.readPackets = int(netSplit[1])
            self.readErrs = int(netSplit[2])
            self.readDrop = int(netSplit[3])
            self.reafFifo = int(netSplit[4])
            self.readFrames = int(netSplit[5])
            self.readCompressed = int(netSplit[6])
            self.readMulticast = int(netSplit[7])   
            
            #parse write info
            self.writeBytes = int(netSplit[8])
            self.writePackets = int(netSplit[9])
            self.writeErrs = int(netSplit[10])
            self.writeDrop = int(netSplit[11])
            self.writeFifo = int(netSplit[12])
            self.writeFrames = int(netSplit[13])
            self.writeCompressed = int(netSplit[14])
            self.writeMulticast = int(netSplit[15].rstrip() )   
            
            #doe Kbs calcs
            if self.__timeDiff > 0:
                self.readBps = ((self.readBytes - self.__lastReadBytes) / self.__timeDiff)
                self.writeBps = ((self.writeBytes - self.__lastWriteBytes) / self.__timeDiff)
                
        #Bad interface name    
        else:
            print "Name:" + name + "Not in file!"

    """Output
        inputs - self - reference for this class instance
        
        description - prints all the information currently stored in this instance.
    """        
    def output(self):
            print "Read information:\n"
            
            print "b/s: ", self.readBps
            print "Bytes: ", self.readBytes
            print "Packets: ", self.readPackets 
            print "Errs: ", self.readErrs
            print "Drop: ", self.readDrop
            print "FIFO: ", self.reafFifo
            print "Frames: ", self.readFrames
            print "Compressed: ", self.readCompressed
            print "Multicast: ", self.readMulticast   
            
            print "\n\nWrite information:\n"
            
            print "b/s: ", self.writeBps
            print "Bytes: ", self.writeBytes
            print "Packets: ", self.writePackets 
            print "Errs: ", self.writeErrs
            print "Drop: ", self.writeDrop
            print "FIFO: ", self.reafFifo
            print "Frames: ", self.writeFrames
            print "Compressed: ", self.writeCompressed
            print "Multicast: ", self.writeMulticast 
     
#test for eth1 just loops forever printing the b/s if it is greater than 0       
if __name__ == "__main__":

    cm = ConnectionMonitor("eth1")
    
    while True:
        cm.update()
        
        if cm.readBps > 0:
            print "Read b/s: ", cm.readBps
            print "Bytes: ", cm.readBytes
        if cm.writeBps > 0:
            print "Write b/s: ", cm.writeBps
            print "Bytes: ", cm.writeBytes
        time.sleep(1)
[/PHP]

---


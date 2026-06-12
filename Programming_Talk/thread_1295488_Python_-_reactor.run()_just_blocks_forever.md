---
title: "Python - reactor.run() just blocks forever"
date: 2009-10-19
forum: Programming Talk
---

### Post by kaivalagi on 2009-10-19
Hi All,

I am hoping someone reading this has had prior experience with twisted reactor in python. I have a strange issue I can't seem to figure out...here goes...

Now that deluge 1.2.0 is out, deluge is now using twisted to provide for what is known as DelugeRPC. I can successfully use async callbacks to connect and fetch data from deluge when done from a simple class based script.

However if I then take effectively the same code and use it in a module I then import into another script, reactor.run() just blocks forever. The same .py file I am importing can be called directly and works :confused:

So my question really comes down to why reactor might have issue with running in an imported module when it is fine in a top level script???

A snippet of the code is as follows (not runnable - to have that you would need a large amount of my source), the line in red is what blocks:

```
class DelugeInfo:
        
    def __init__(self, options):

        try:

            self.options = options

            # create the rpc and client objects
            self.d = client.connect(self.options.server, self.options.port)

            # We add the callback (in this case it's an errback, for error)
            self.d.addErrback(self.on_connect_fail)
            
            # We add the callback to the Deferred object we got from connect()
            self.d.addCallback(self.on_connect_success)
            
            [COLOR="Red"]reactor.run()[/COLOR]

        except Exception,e:
            self.logError("DelugeInfo Init:Unexpected error:" + e.__str__())

    def on_get_torrents_status(self,torrents_status):
        
        self.torrents_status = torrents_status
        
        # Disconnect from the daemon once we successfully connect
        client.disconnect()
        # Stop the twisted main loop and exit
        reactor.stop()
        
    # We create a callback function to be called upon a successful connection
    def on_connect_success(self,result):
        self.logInfo("Connection successful")
        client.core.get_torrents_status("","").addCallback(self.on_get_torrents_status)
                
    # We create another callback function to be called when an error is encountered
    def on_connect_fail(self,result):
        self.logError("ERROR:Connection failed! : "+result)
```

---


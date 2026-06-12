---
title: "Python Twisted: Disconnection"
date: 2010-10-17
forum: Programming Talk
---

### Post by Sailor5 on 2010-10-17
Ahoy Sailors!

So to simplify this right from the start, When someone connects to my Host script, They first send a string with their PC name attached.

```
n:JoeyBlowHole-PC
```We'll store this into a variable, Along with any others that are being sent. So it may look like this.

```
JoeyBlowHole-PC:JohnBinBag-PC
```Now I'm needing to print to terminal a disconnection message.

```
<PcName> Has disconnected!
```But there's the problem, When someone disconnects how do I know which PC name to print to console?

Thanks Bye!

---

### Post by mo.reina on 2010-10-17
> **Sailor5 said:**
> Ahoy Sailors!

So to simplify this right from the start, When someone connects to my Host script, They first send a string with their PC name attached.

```
n:JoeyBlowHole-PC
```We'll store this into a variable, Along with any others that are being sent. So it may look like this.

```
JoeyBlowHole-PC:JohnBinBag-PC
```Now I'm needing to print to terminal a disconnection message.

```
<PcName> Has disconnected!
```But there's the problem, When someone disconnects how do I know which PC name to print to console?

Thanks Bye!

are you using factories?

if you are, the function clientConnectionFailed requires a parameter called connector, which is the protocol instance.

another way, still in the factory, is to print out self.host and self.port (assuming of course you've assigned these variables to the host and port in __init__)

---

### Post by Sailor5 on 2010-10-18
> **mo.reina said:**
> are you using factories?

if you are, the function clientConnectionFailed requires a parameter called connector, which is the protocol instance.

another way, still in the factory, is to print out self.host and self.port (assuming of course you've assigned these variables to the host and port in __init__)

```
class EchoServerFactory(ServerFactory):
   protocol = Chimera
   def clientConnectionLost(self, connector, reason):
       print connector
   
   def clientConnectionMade(self,broker): 
       print "Connection!"
 
def main():
    f = EchoServerFactory()
    reactor.listenTCP(port, f)
    reactor.run()

if __name__ == '__main__':
    main()
```Thanks for replying But I don't get either the string 'Connection!' or the connector being printed to terminal, Is there something wrong with my code?

---


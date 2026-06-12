---
title: "Java.. cant move an Enum to a ByteBuffer"
date: 2011-02-28
forum: Programming Talk
---

### Post by bcz on 2011-02-28
Hi all

Am trying to dump a class to a ByteBuffer.

Am using Enums in the class and cant find a way to do it with latest J2SE on Ubuntu 10.10

Compiles with an inconvertible type message.  Is the answer to forget about using enums in Java at this point in time, or is there a way to do it


```
//      Simple page structure

import java.awt.*;
import java.nio.*;

class Simp extends Object{

public enum IpType{P0,IX,DT,DB;}

IpType tag,type;
Byte updated;
static ByteBuffer stgB;
int blk;

private Simp(int pgSize){
        tag=IpType.DB; type=IpType.P0; updated=0; blk=0;}

private int dump(){
        stgB=ByteBuffer.allocate(256);
        stgB.put((int)tag);
        stgB.put((int)type);
        stgB.put(updated);
        stgB.putInt(blk);
        return stgB.position();}

}

```

Any thoughts?

---

### Post by t1497f35 on 2011-02-28
It looks like you're trying to serialize a class, if so, Java already has built-in support, just google around.

---

### Post by bcz on 2011-02-28
Thanks t149...

What I am doing is very similar to serialiation.

Am writing an ISAM type record handler, and need to pack records into datapages.  This is just a general case which naturally used enums.  Simply solved/avoided by replacing enums with "static Byte P0=1; ..."

I talk to the ISAM record handler using sockets and serialization.  I dont really want to impose a reader/writer overhead on simply moving records around and ByteBuffer gives me most of the functionality I want, maybe at 50% the efficiency of using C.  Still way more efficient than RDMS systems.

Thanks Bill

---

### Post by PaulM1985 on 2011-03-01
I have found that ObjectInputStreams and ObjectOutputStreams are very useful and have little overhead to converting my data into byte streams.

Given a little testing you may find that there isn't much difference and that you code is alot simpler.

Paul

---

### Post by Some Penguin on 2011-03-01
[http://download.oracle.com/javase/6/docs/api/java/lang/Enum.html#ordinal()]("http://download.oracle.com/javase/6/docs/api/java/lang/Enum.html#ordinal()")

---


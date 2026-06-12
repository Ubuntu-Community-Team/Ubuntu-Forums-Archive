---
title: "Need android help (java)"
date: 2010-01-19
forum: Programming Talk
---

### Post by WitchCraft on 2010-01-19
I do a:

```

java.net.InetAddress serverAddr;
try {
    serverAddr = java.net.InetAddress.getByName(Server.SERVERNAME);
}
catch (java.net.UnknownHostException exception) {
    //System.err.println ("wrong server name !!!");
    HelloWorldActivity.tv.setText("wrong server name !!!");
    return;
}

```
in my android application, but it's never resoling the hostname, it always throws an exception, no matter what name I use.


But using the internet on the same emulator works, and I've added
```

<use-permission id="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

```
to AndoidManifest.xml

and here's the server class for those who assume I have none

```

public class Server
{
    public static String SERVERNAME = "monster.idsoftware.com";
    public static String SERVERIP = "209.85.129.99";
    public static int SERVERPORT = 27950;
    public static int PROTOCOL = 68;
}

```

---

### Post by WitchCraft on 2010-01-21
bump.

---

### Post by hoboy on 2010-01-21
I think that you will have better luck to get reply here 
[http://groups.google.com/group/android-beginners](http://groups.google.com/group/android-beginners)

---

### Post by WitchCraft on 2010-01-21
> **hoboy said:**
> I think that you will have better luck to get reply here 
[http://groups.google.com/group/android-beginners](http://groups.google.com/group/android-beginners)

I fear that most likely it's a bug in android's Dalvik VM.

---


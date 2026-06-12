---
title: "Sync gcaldaemon and Evolution"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Ventiakan on 2008-09-12
I am a newbie trying to set up gcaldaemon in Hardy Heron to sync with Google calendar. I have followed the instructions in the user guide and have got as far as using ./standalone-start.sh

The start up begins okay but then it produces the following error

INFO  | Mail terminal disabled. 
Exception in thread "Timeout guard" java.lang.NullPointerException 
   at gnu.javax.net.ssl.provider.SSLEngineImpl.<init>(libgcj.so.81) 
   at gnu.javax.net.ssl.provider.SSLSocketImpl.<init>(libgcj.so.81) 
   at gnu.javax.net.ssl.provider.SSLSocketImpl.<init>(libgcj.so.81) 
   at gnu.javax.net.ssl.provider.SSLSocketFactoryImpl.createSocket(libgcj.so.81) 
   at gnu.javax.net.ssl.provider.SSLSocketFactoryImpl.createSocket(libgcj.so.81) 
   at org.apache.commons.httpclient.protocol.SSLProtocolSocketFactory.createSocket(SSLProtocolSocketFactory.java:81) 

followed by a couple of pages of other stuff.

Can anyone tell me what I might have done wrong?

Thanks

---


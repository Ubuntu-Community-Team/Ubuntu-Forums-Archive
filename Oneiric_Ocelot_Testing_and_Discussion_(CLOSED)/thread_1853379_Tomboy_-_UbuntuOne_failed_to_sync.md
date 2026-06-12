---
title: "Tomboy - UbuntuOne failed to sync"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-10-02
I'm not able to sync tomboy notes with online UbuntuOne service.
Is there any bug report for this?

```
02/10/2011 13.38.38 [INFO]: Initializing Mono.Addins
02/10/2011 13.38.40 [ERROR]: Unparsable last-sync-date element in /home/luca/.config/tomboy/manifest.xml
02/10/2011 13.39.01 [ERROR]: Error processing OAuth callback. Could be a sign that you pressed the button to reset the connection. Exception details:
02/10/2011 13.39.01 [ERROR]: System.ObjectDisposedException: The object was used after being disposed.
  at System.Net.ListenerAsyncResult.GetContext () [0x00000] in <filename unknown>:0 
  at System.Net.HttpListener.EndGetContext (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at Tomboy.WebSync.WebSyncPreferencesWidget.<OnAuthButtonClicked>m__1 (IAsyncResult localResult) [0x00000] in <filename unknown>:0 
02/10/2011 13.39.58 [ERROR]: Error cleaning up addin after sync: Object reference not set to an instance of an object
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] in <filename unknown>:0 
02/10/2011 13.40.46 [ERROR]: Caught exception. Message: The remote server returned an error: (400) BAD REQUEST.
02/10/2011 13.40.46 [ERROR]: Stack trace for previous exception:   at System.Net.HttpWebRequest.CheckFinalStatus (System.Net.WebAsyncResult result) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.SetResponseData (System.Net.WebConnectionData data) [0x00000] in <filename unknown>:0 
02/10/2011 13.40.46 [ERROR]: Rest of stack trace for above exception:    at System.Environment.get_StackTrace()
   at Tomboy.WebSync.Api.OAuth.MakeWebRequest(RequestMethod method, System.String url, System.Collections.Generic.List`1 parameters, System.String postData)
   at Tomboy.WebSync.Api.OAuth.WebRequest(RequestMethod method, System.String url, System.String postData)
   at Tomboy.WebSync.Api.OAuth.Post(System.String uri, IDictionary`2 queryParameters, System.String postValue)
   at Tomboy.WebSync.Api.OAuth.GetAccessAfterAuthorization()
   at Tomboy.WebSync.WebSyncPreferencesWidget.<OnAuthButtonClicked>m__1(IAsyncResult localResult)
   at System.Net.ListenerAsyncResult.InvokeCallback(System.Object o)
02/10/2011 13.40.57 [ERROR]: Error cleaning up addin after sync: Object reference not set to an instance of an object
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] in <filename unknown>:0 
```

---

### Post by lucazade on 2011-10-03
bugreport:

[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/865197](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/865197)

---


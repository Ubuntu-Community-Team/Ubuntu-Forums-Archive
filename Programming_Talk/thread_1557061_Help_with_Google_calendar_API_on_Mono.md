---
title: "Help with Google calendar API on Mono"
date: 2010-08-20
forum: Programming Talk
---

### Post by Newbie2910 on 2010-08-20
I can't figure out why this code:

try
            {
                   // Authenticate
                   CalendarService calService = new CalendarService("cl");
   string name = (hidden);  
   string pass = (hidden);
                   calService.setUserCredentials(name, pass);

   string token = calService.QueryAuthenticationToken(); 
   ...

works fine (token is a valid Google authorization token) under Windows but on Mono token always comes back as null.

I am using the same Google .DLLs on both systems (in fact, it's the same PC with Windows Vista/Ubuntu dual-boot).

This is driving me crazy... it always works, I can read/write calendar  items all day long under Windows but the same code running on Mono on  Ubuntu will not authenticate.  The exception always comes back as "401  Authentication required".

Help!

---

### Post by Newbie2910 on 2010-08-20
I found this link while searching:

[http://groups.google.com/group/gdata-dotnet-client-library/browse_thread/thread/6418b441d8fc6238/520defa0346877d9?lnk=gst&q=mono#520defa0346877d9](http://groups.google.com/group/gdata-dotnet-client-library/browse_thread/thread/6418b441d8fc6238/520defa0346877d9?lnk=gst&q=mono#520defa0346877d9)

Does this sound right?  I guess I have to read up on adding these certificates.

I ran this command:

mozroots --import --ask-remove

and

certmgr -ssl smtps://smtp.gmail.com:465

So now I don't get an authentication error, however the app slows to a glacial crawl... eventually (5-8 minutes later) the debugger comes back to life to indicate a general Google error (no specifics).  I did set the EventQuery to use SSL.

WTF?

---


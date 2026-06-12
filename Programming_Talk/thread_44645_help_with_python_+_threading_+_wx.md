---
title: "help with python + threading + wx"
date: 2005-06-27
forum: Programming Talk
---

### Post by sapo on 2005-06-27
hi fellows.. i ve started with python some days ago.. and my first app is working..

But i cant find anything easy to understand about running processes on the background and getting their status.. the output would be nice too

i m running the process with this:

```

                self.process = wxProcess( self )
                self.process.Redirect()
                self.pid = wxExecute( i, wxEXEC_SYNC, self.process )

```

I want to run it with the wxEXEC_ASYNC option.. and get its status to, if possible use a progress bar.. 

i ve found this script that uses progress bar and stuff.. but i didnt understand it very well...

[http://staffa.wi.mit.edu/people/kelley/Process.py](http://staffa.wi.mit.edu/people/kelley/Process.py)

is there a simple way to do it?

even if its just to run in backgound and make a "dummy" progress bar... 

My script is here:
[http://xgn.no-ip.org:1000/downloads/converter.py](http://xgn.no-ip.org:1000/downloads/converter.py)

its working.. i ve made a dummy progress bar but it just updates when one command finishes, cause it have to wait for it to finish  ](*,)

---


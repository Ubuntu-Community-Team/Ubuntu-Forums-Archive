---
title: "Colouring the output of tail -f"
date: 2009-04-17
forum: Programming Talk
---

### Post by JeppeM on 2009-04-17
Hey all,

I have a team of developers who all use Ubuntu for developing our different Java applications... Often, we have windows like tail -f /opt/tomcat/log/catalina.out open, which gives output like this:

```

INFO: ApplicationComponent 'statistics_rmiClient' initialization started.
Apr 17, 2009 11:41:44 AM com.polopoly.application.RmiApplicationComponentImpl doInit
INFO: statistics_rmiClient, rmiEnvironment: <providerUrl='rmi://localhost:1199', initialContextFactory='com.sun.jndi.rmi.registry.RegistryContextFactory'>
Apr 17, 2009 11:41:44 AM com.polopoly.application.AbstractApplicationComponentControl realize
INFO: statistics_rmiClient connected and started serving, state is <status: CONNECTED and SERVING, requested: CONNECTED and SERVING>.
Apr 17, 2009 11:41:44 AM com.polopoly.application.ApplicationComponentImpl init
INFO: ApplicationComponent 'statistics_rmiClient' initialization finished.
Apr 17, 2009 11:41:44 AM com.polopoly.application.StandardApplication init
INFO: Application 'statisticsGui' initialization finished.
Apr 17, 2009 11:41:44 AM org.apache.coyote.http11.Http11BaseProtocol start
INFO: Starting Coyote HTTP/1.1 on http-8080
Apr 17, 2009 11:41:44 AM org.apache.jk.common.ChannelSocket init
INFO: Port busy 8009 java.net.BindException: Address already in use
Apr 17, 2009 11:41:44 AM org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8010
Apr 17, 2009 11:41:44 AM org.apache.jk.server.JkMain start
INFO: Jk running ID=1 time=0/27  config=null
Apr 17, 2009 11:41:44 AM org.apache.catalina.storeconfig.StoreLoader load
INFO: Find registry server-registry.xml at classpath resource
Apr 17, 2009 11:41:44 AM org.apache.catalina.startup.Catalina start
INFO: Server startup in 12819 ms
Apr 17, 2009 11:58:46 AM com.polopoly.service.cm.basic.server.ContentRepositoryCaching$ManagementServiceListener syncCache
INFO: Found 1067 changed contents.
Apr 17, 2009 11:58:46 AM com.polopoly.service.cm.basic.server.ContentRepositoryCaching$ManagementServiceListener syncCache
INFO: Synced 0/1067
Apr 17, 2009 11:58:54 AM com.polopoly.service.cm.basic.server.ContentRepositoryCaching$ManagementServiceListener syncCache
INFO: Synced 1000/1067
Apr 17, 2009 11:58:55 AM com.polopoly.service.cm.basic.server.ContentRepositoryCaching$ManagementServiceListener syncCache
INFO: Synced 1067 contents.
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: ignoreErrors=false
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: holdResponse=true
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: trackUsers=false
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: renderStatsHistory=0
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: (static) userHistory=0
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: (static) prospects=0
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: dispatch count=1
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: request count=1
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: hasKeyCnt=0
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: noKeyCnt=0
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: cacheHitCnt=0
Apr 17, 2009 11:58:56 AM com.polopoly.render.AbstractRenderDispatcher logStats
INFO: dispatcherId=AbstRendDisp1: cacheMissCnt=0
Apr 17, 2009 11:58:56 AM org.apache.velocity.tools.view.servlet.ServletToolboxManager getInstance
INFO: Using config file '/WEB-INF/toolbox.xml'

```

I would like to hear if there's a way to use the gnome-terminal, or perhaps something like, to make this output easier to read, using colours. For example, it would be really nice if we could have the date appear in light grey, the class appear in dark grey, an info lines in black, but any WARNING or SEVERE lines in red...

Is there any way this is possible?

---

### Post by odyniec on 2009-04-17
You could pipe the output to sed and have it insert ANSI escape codes around specific parts of the text to change their color. For example, the following command will make the line red if "WARNING" is in the text:
```
tail -f /opt/tomcat/log/catalina.out | sed 's/^\(.*WARNING.*\)$/\x1b[0;31m\1\x1b[0m/'
```

The "\x1b[0;31m" sequence indicates that all the characters that follow should be displayed in red, up to "\x1b[0m", which sets back the default color.

For more information on the escape codes, see [http://en.wikipedia.org/wiki/ANSI_escape_code](http://en.wikipedia.org/wiki/ANSI_escape_code).

---

### Post by JeppeM on 2009-04-17
ah! very nice indeed... I just tried it out, and it looks very promissing.. thanks a lot odyniec!

---

### Post by JeppeM on 2009-04-17
Ok, just tried it out a bit, and i can't get sed to work for tail -f, only tail -n 200... I found that perl can do the same though, and it works with tail -f, however, i can only get it to work with one argument... If i do

```

tail -f /opt/tomcat/logs/catalina.out | perl -p -e 's/^(\w{3} \w{2}, \w{4}.*)/\x1b[0;32m\1\x1b[0m/;'

```

However, since i want different colours on different things, i tried to do this:

```

tail -f /opt/tomcat/logs/catalina.out | perl -p -e 's/^(\w{3} \w{2}, \w{4}.*)/\x1b[0;32m\1\x1b[0m/;' | perl -p -e 's/^(INFO.*)/\x1b[0;32m\1\x1b[0m/;' | perl -p -e 's/^(\s+.*)/\x1b[1;31m\1\x1b[0m/;' | perl -p -e 's/^(WARNING.*)/\x1b[1;35m\1\x1b[0m/;' | perl -p -e 's/^(SEVERE.*)/\x1b[1;31m\1\x1b[0m/;' | perl -p -e 's/^(.*Exception:.*)/\x1b[1;31m\1\x1b[0m/;'

```

Which doesn't display anything... What am i doing wrong here? :/

---

### Post by Arndt on 2009-04-17
> **JeppeM said:**
> Ok, just tried it out a bit, and i can't get sed to work for tail -f, only tail -n 200... 


Does it work if you use the -u flag to 'sed'? The output needs to be unbuffered, or you will get the data in 1024 or 2048 byte chunks.

---

### Post by JeppeM on 2009-04-17
It works! very cool :D Thanks a lot for your help...

---

### Post by jordilin on 2009-05-21
I have the same problem and I use [http://code.google.com/p/log4tailer/](http://code.google.com/p/log4tailer/)
which works very well for me

---


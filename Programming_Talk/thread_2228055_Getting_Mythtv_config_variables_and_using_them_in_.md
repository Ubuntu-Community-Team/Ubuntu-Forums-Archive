---
title: "Getting Mythtv config variables and using them in php"
date: 2014-06-05
forum: Programming Talk
---

### Post by bonelifer on 2014-06-05
I would like to read in the configuration variables from the mythtv "config.xml" file. I've tried SimpleXML, but not sure how to use the data after I get it to use it to connect to mysql.  Here's the current file with the info hardcoded.  [http://pastebin.com/hhKbeVUX](http://pastebin.com/hhKbeVUX)   I'm not a coder, so I'm currently at my wits end from looking at all sorts of examples online.


path: /home/mythtv/.mythtv/config.xml

example config.xml
```
<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <!--
Set the <LocalHostName> hostname override below only if you want to use
something other than the machine's real hostname for identifying settings
in the database.  This is useful if your hostname changes often, as
otherwise you'll need to reconfigure mythtv every time.

NO TWO HOSTS MAY USE THE SAME VALUE
-->
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
  <LocalHostName>my-unique-identifier-goes-here</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>localhost</Host>
    <UserName>mythtv</UserName>
    <Password>mypass</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>
```

---

### Post by bonelifer on 2014-06-05
Nevermind found what I needed. After what feels like millions of useless usage examples.

---


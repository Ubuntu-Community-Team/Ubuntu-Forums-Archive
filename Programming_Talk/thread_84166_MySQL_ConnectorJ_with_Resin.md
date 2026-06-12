---
title: "MySQL Connector/J with Resin"
date: 2005-10-30
forum: Programming Talk
---

### Post by matthurne on 2005-10-30
Hello All,
   I'm working on setting up a webapp on Breezy.  I thus have MySQL 4.1.12, the Sun JDK 1.5.0_05, Apache 2.0.54, Resin 3.0.14, and Connector/J 3.1.11.  I set up Resin to service servlets/jsp as an Apache module, which was hell enough.  I configured Resin to give each user a webapp at hostname/~user/ .  Yada yada yada - all that should be unrelated, I would think.  Now to the problem.  It seems that the whole setup is working fine to read from the database, but upon trying to insert data, I get the following from Resin:

```

500 Servlet Exception

com.mysql.jdbc.CommunicationsException: Communications link failure due
to underlying exception: 

** BEGIN NESTED EXCEPTION ** 

java.io.EOFException

STACKTRACE:

java.io.EOFException
	at com.mysql.jdbc.MysqlIO.readFully(MysqlIO.java:1903)
	at com.mysql.jdbc.MysqlIO.reuseAndReadPacket(MysqlIO.java:2349)
	at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:2860)
	at com.mysql.jdbc.MysqlIO.sendCommand(MysqlIO.java:1571)
	at com.mysql.jdbc.ServerPreparedStatement.serverExecute(ServerPreparedStatement.java:1120)
	at com.mysql.jdbc.ServerPreparedStatement.executeInternal(ServerPreparedStatement.java:675)
	at com.mysql.jdbc.PreparedStatement.execute(PreparedStatement.java:773)
	at _jsp._albumSave__jsp._jspService(_albumSave__jsp.java:64)
	at com.caucho.jsp.JavaPage.service(JavaPage.java:60)
	at com.caucho.jsp.Page.pageservice(Page.java:570)
	at com.caucho.server.dispatch.PageFilterChain.doFilter(PageFilterChain.java:159)
	at com.caucho.server.webapp.WebAppFilterChain.doFilter(WebAppFilterChain.java:163)
	at com.caucho.server.dispatch.ServletInvocation.service(ServletInvocation.java:208)
	at com.caucho.server.hmux.HmuxRequest.handleRequest(HmuxRequest.java:396)
	at com.caucho.server.port.TcpConnection.run(TcpConnection.java:363)
	at com.caucho.util.ThreadPool.runTasks(ThreadPool.java:490)
	at com.caucho.util.ThreadPool.run(ThreadPool.java:423)
	at java.lang.Thread.run(Thread.java:595)


** END NESTED EXCEPTION **



Last packet sent to the server was 14 ms ago.
	at com.mysql.jdbc.MysqlIO.reuseAndReadPacket(MysqlIO.java:2561)
	at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:2860)
	at com.mysql.jdbc.MysqlIO.sendCommand(MysqlIO.java:1571)
	at com.mysql.jdbc.ServerPreparedStatement.serverExecute(ServerPreparedStatement.java:1120)
	at com.mysql.jdbc.ServerPreparedStatement.executeInternal(ServerPreparedStatement.java:675)
	at com.mysql.jdbc.PreparedStatement.execute(PreparedStatement.java:773)
	at _jsp._albumSave__jsp._jspService(albumSave.jsp:33)
	at com.caucho.jsp.JavaPage.service(JavaPage.java:60)
	at com.caucho.jsp.Page.pageservice(Page.java:570)
	at com.caucho.server.dispatch.PageFilterChain.doFilter(PageFilterChain.java:159)
	at com.caucho.server.webapp.WebAppFilterChain.doFilter(WebAppFilterChain.java:163)
	at com.caucho.server.dispatch.ServletInvocation.service(ServletInvocation.java:208)
	at com.caucho.server.hmux.HmuxRequest.handleRequest(HmuxRequest.java:396)
	at com.caucho.server.port.TcpConnection.run(TcpConnection.java:363)
	at com.caucho.util.ThreadPool.runTasks(ThreadPool.java:490)
	at com.caucho.util.ThreadPool.run(ThreadPool.java:423)
	at java.lang.Thread.run(Thread.java:595)

Resin-3.0.14 (built Tue, 05 Jul 2005 11:03:36 PDT)

```

I've really busted my butt looking for a solution.  I google'd, searched these forums, etc.  I found a few threads that talked about some problems on Ubuntu and went ahead with their suggestions, to no avail - I check my.cnf for "skip-networking" and it has "bind-address 127.0.01" instead, I swapped the order of "localhost" and "localhost.localdomain" in my /etc/hosts . . .

In my application, I use the following code to connect to MySQL:

```

  Class.forName("com.mysql.jdbc.Driver").newInstance();
  Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/dbname", "username", "password");

```

With the appropriate dbname, username and password, of course.  I had also experimented with the apparently preferred method of connection pooling and connecting via JNDI, but I get the exact same behavior that way, so it doesn't seem to matter which I use.

I've read in my searches that it may have something to do with stale connections and MySQL's "wait_timeout", but I don't really understand that nor what to do about it if that is part of the problem.

Thanks guys.

---


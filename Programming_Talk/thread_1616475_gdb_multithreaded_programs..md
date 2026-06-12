---
title: "gdb multithreaded programs."
date: 2010-11-08
forum: Programming Talk
---

### Post by DuneSoldier on 2010-11-08
Hi, also this is going to be a useless thread until I get home and have access to the source code again.

Basically I've got a little C++ app that I put together to allow you to connect to a TCP port on a PC and talk to a serial port on the PC. I bought a Beagleboard XM a little while ago and this was just kind of a fun project to get working on it.

I start the app, and spawn off a thread to listen on a port in the CommandServer object. When someone connects they are able to issue some commands to get a list of all the serial devices in the PC and issue a link command like:

"link /dev/ttyUSB0 2000"

Then you can connect via TCP on 2000 and everything coming off the serial port will be sent to you and everything you send will go out on the serial.

It works, runs (and crashes when you disconnect.) but I can't run it in gdb or ddd. I see a couple of "New Thread" messages and then gdb just sits there. If I connect to the CommandServer via TCP it allows me to connect but doesn't respond to any commands.

I'm not sure how to troubleshoot this. I'll tar and upload the code when I get home if anyone wants to give me a hand.

Also I'm using boost::thread, and boost::asio libraries as well as the boost::filesystem library to scan for serial devices under /dev

---

### Post by DuneSoldier on 2010-11-08
Alright, this is far from finished. IE I'm doing next to nothing with the serial port apart from opening it and reading/writing to it.

But here's what I see when I connect to the port (5000) using telnet outside of the debugger:

So I call ./ipserialbridge 5000

```

phillip@Remote:~/Desktop$ telnet localhost 5000
Trying 127.0.0.1...
Connected to Remote.
Escape character is '^]'.
Welcome to IP Serial Bridge!
Command:help
Help Acceptable Commands
Help - You're looking at it.
List Devices - Show all available serial ports
List Links - Show Current Links
Link <device> <port> - link the TCP Port to the Device on the System
Unlink <device> - unlink the TCP Port
Shutdown - Shutsdown the IP Serial Bridge

Command:


```

Starting it using gdb

```

phillip@Remote:~/Projects/ipserialbridge/src$ gdb --args ./ipserialbridge 5000
GNU gdb (GDB) 7.2-debian
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/phillip/Projects/ipserialbridge/src/ipserialbridge...done.
(gdb) run
Starting program: /home/phillip/Projects/ipserialbridge/src/ipserialbridge 5000
[Thread debugging using libthread_db enabled]
[New Thread 0xb7cddb70 (LWP 5225)]
[New Thread 0xb74dcb70 (LWP 5226)]



```

and when I attempt to connect via telnet on port 5000

```

phillip@Remote:~/Desktop$ telnet localhost 5000
Trying 127.0.0.1...
Connected to Remote.
Escape character is '^]'.


```

So I can connect but I'm not seeing my friendly little welcome message. Nor is gdb prompting me for anything. Any ideas on why this might be the case?

Oh and I used autotools for this project (I strongly reccommend "Autotools" by John Calcote) so you should just be able to do a ./configure and make if you are interested.

---

### Post by DuneSoldier on 2010-11-08
Alright I've tracked it down somewhat at least. In this code, I never see "Handle Incoming Called" when running in the debugger. I do see "Handle Incoming connected up". So my original post was wrong, gdb isn't hanging, but my acceptor method isn't being called.

```

	void CommandServer::runServer()
	{
		m_Acceptor.reset(new boost::asio::ip::tcp::acceptor(m_IOService,boost::asio::ip::tcp::endpoint(boost::asio::ip::tcp::v4(),m_Port)));

		boost::shared_ptr<boost::asio::ip::tcp::socket> sock(new boost::asio::ip::tcp::socket(m_IOService));
		m_Acceptor->async_accept(*(sock.get()),boost::bind(&CommandServer::handleIncoming,this, boost::asio::placeholders::error,sock));
		std::cout << "Handling Incoming connected up" << std::endl;
	}

	void CommandServer::handleIncoming(const boost::system::error_code & _e,boost::shared_ptr<boost::asio::ip::tcp::socket> _sock)
	{
		if(!_e)
		{
		  std::cout << "Handle Incoming Called" << std::endl;
			boost::shared_ptr<CommandSession> m(new CommandSession(_sock));

			boost::function<void (IPCommand *, CommandSession *)> func(boost::bind(&CommandServer::handleCommand,this,_1, _2));

			m->connectCommandSignal(func);

			std::string output("Welcome to IP Serial Bridge!");
			m->write(output);
			m->displayPrompt();

			m_Sessions.push_back(m);
			std::cout << "Session Created!" << std::endl;
		}

		boost::shared_ptr<boost::asio::ip::tcp::socket> sock(new boost::asio::ip::tcp::socket(m_IOService));
		m_Acceptor->async_accept(*(sock.get()),boost::bind(&CommandServer::handleIncoming,this,boost::asio::placeholders::error, sock));
	}

```

---

### Post by DuneSoldier on 2010-11-09
Hmmm, can't seem to figure out what's going on at this point. Googling is only showing this thread for gdb boost asio acceptor problems.

Is there a way to attach the gdb later in the applications life? I've got a segfault I'm trying to track down.

---

### Post by DuneSoldier on 2010-11-09
never mind found the attach syntax. Seems to let me play as long as I attach after that point in the program.

---


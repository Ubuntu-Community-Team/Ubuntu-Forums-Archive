---
title: "script to submit form data over https"
date: 2006-09-25
forum: Programming Talk
---

### Post by rjs on 2006-09-25
g'day all,

I live on campus at my uni. To access teh interweb we have two options; a programme that we download or a web based logon. The programme provided for linux is absolute crud. I managed after much work to get it working on my computer but i have recently installed ubuntu on a friends box and can't get it running for them (see the end for a discription of just how badly written a programme can be). Anyway, what i want is to write a script to submit the web-based form for me automatically on startup (and perhaps even output how much credit i have left). So, what i want to know is what librarys exist that can be used to interact with web-based forms (that is the standard html <form> element) in whatever your favorite scripting language is (unless it's java)? I want to use this problem as a chance to expand my programming skills so i don't really mind the language (though since i already know basic ruby that would be prefered).

All my web searching has so far just picked up CGI stuff, but that's all (as i understand it) used for a server interacting with a user-agent whereas i want something which is a user-agent interacting with a server.

paz,
-rjs.

What was wrong with the supplied (command-line) programme: Instructions say unpack the tar.gz into ~/ and you'll be right. The programme is actually a collection of 4 programmes and (i think) 2 config files. The programmes complain if they can't find each other in /usr/local/bin. However if you move everything to /usr/local/bin they complain that they can't find the config files in ~/ (actually not ~/ but the pwd, but the errors don't say pwd so you only work that out when you try to start it one time without being in ~/). On top of these stupidities there must be something else that i have forgotten cause i can't get it to work on my friends box.

in case you are wondering the web-based form i want to interact with is here: https:150.203.204.18/sdas.php (i don't know if it accessable from outside the ANU network or not).

---

### Post by ohgod on 2006-09-25
Well, I don't know ruby, but it looks like you could do this with the Net::HTTP library:  [http://www.ruby-doc.org/stdlib/libdoc/net/http/rdoc/classes/Net/HTTP.html]("http://www.ruby-doc.org/stdlib/libdoc/net/http/rdoc/classes/Net/HTTP.html")

---

### Post by rjs on 2006-09-25
Exactly what i was looking for. Thanks a lot. You're a legend.

paz,
-rjs.

---


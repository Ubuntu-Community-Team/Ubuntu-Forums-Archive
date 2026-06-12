---
title: "Programming bottom up (by Paul Graham on Lisp) and design methodology in general"
date: 2012-02-12
forum: Programming Talk
---

### Post by hoangtu on 2012-02-12
Note: Text written in **bold** means my  question. Sorry for the long post, but I want things to be clear with a  concrete example, rather than discussion on vague ideas.

  As I understand, top-down design is by refining the abstract high  level concept into smaller concrete and comprehensible parts, until the  smallest building block is defined. 
  On the other hand, bottom up defines low level parts, then gradually  build up higher level blocks until the whole system is formed.

  In practice, it is said best to combine the two methods: starts with  high level specification to fully specify the domain knowledge, its  relationship and constraints. Once the problem is well understood,  smallest building blocks are created to build up the system. 

  The process of:
  
[LIST]
[*]Creating requirement spec
[*]Create a design spec (with diagrams)
[*]Implement
[*]Deliver
[*]Repeat (in iterative development, rather than doing a whole chunk in  each phase, we do a little bit each repeatedly, and got daily meeting  to adapt to customer's dynamic requirement)
[/LIST]
  looks perfectly normal to me (with specs as plans). 

  Let's take an example: Suppose I'm going to write a Web Server. Since  probably all of us have basic understanding of the domain knowledge  (which is about server and network), I won't write requirement spec. For  design spec, these components are needed to define (from the  perspective of C++):
  
[LIST]
[*]Server: A component to unite related components.
[*]Acceptor: To accept connection and identify what type of connection is (HTTP, FTP...)
[*]Connection Manager: To manage connections, include storing a  collection of connections, and process connection according to each of  its states (such as alive/not responding/time out).
[*]Connection: Represent each connection, and takes care of basic actions like send/receive data.
[*]Session Manager: Manage the session data of each connection. It associates state data with a reference to each connection.
[*]Module Manager: Manage how the server is adapted to user created module in order to exten its functionality.
[/LIST]
  After the overview of each component, I further refine each into lower level details:
  
[LIST]
[*]Acceptor: An abstract class to represent a generic acceptor.
[LIST]
[*]HttpAcceptor: A class to accept and validate if a connection is Http, which connects through port 80.
[*]FtpAcceeptor: Same as HttpAcceptor, except for Ftp and port 22
[/LIST]
 
[*]Connection Manager: A class to keep a collection of active connections and perform said functionalities
[*]Connection: A generic connection class
[LIST]
[*]HttpConnection: Process the request and response of Http messages.
[*]FtpConnection: Process the request and response of Ftp messages.
[/LIST]
 
[*]Session Manager: Use something like std::map to associate session data and a reference of a connection.
[LIST]
[*]SessionData: A class contains the std::map of <Key, Value> pairs for keeping state data of a website. The <Key,Value> pair is implemented using template<class Key, class Value>.
[/LIST]
 
[/LIST]
  This is an oversimplification design I thought on top of my head for  this example based on basic understanding. Of course, it will have  flaws, but that's why we got iterative development: instead of spending  time on one phase, says, requirement analysis to study every possible  thing in domain knowledge which is subjected to changes (possibly  daily), we do a little bit of analysis, a little bit of design and then  implements it, in a day. Another way is that each iteration is a  mini-waterfall fashion, where analysis is done in a few days (or a  week). The same applies for design. The rest of time is spent for  implementation. Then we deliver a build to our clients. 
  If requirement is unclear, we keep study the domain model until we  have a spec which is implementable. I can't imagine jump right into  programming without, even basic, up front planning.
  **What's wrong with top-down approach in combination with iterative development?** 
  In his essay about bottom-up programming, **did Paul Graham  encourage build from bottom up completely? Or just program it from  bottom up, but not the requirement analysis/desing phase?** Because in one of his paragraph, he said:

   > Experienced Lisp programmers divide up their programs differently. As   well as top-down design, they follow a principle which could be called   bottom-up design-- changing the language to suit the problem. As far as I get, what he meant is that Lisper still performs top-down  design, but program bottom up, is that true? Another point he said:

   > It's worth emphasizing that bottom-up design doesn't mean just writing   the same program in a different order. When you work bottom-up, you   usually end up with a different program. Instead of a single,   monolithic program, you will get a larger language with more abstract   operators, and a smaller program written in it. Instead of a lintel,   you'll get an arch. **This means, during the period of writing a program in Lisp,  you end up with a generic tool which can be used to write similar  programs of the original one, doesn't it?**
  I'm going to learn Lisp. Take my server example, how do you design such reusable component in Lisp?

---

### Post by savanna on 2012-02-12
I won't get into the specifics of the component you're trying to design.

However, I will say that I've found that studying LISP has certainly improved my programming - it does make you think in a different way. Check out the SICP book and videos (Scheme not LISP) - it's great.

[http://mitpress.mit.edu/sicp/](http://mitpress.mit.edu/sicp/)

(and a little script to download the SICP videos:
[https://github.com/soniah/get_sicp](https://github.com/soniah/get_sicp))

---

### Post by hoangtu on 2012-02-12
> **savanna said:**
> I won't get into the specifics of the component you're trying to design.

However, I will say that I've found that studying LISP has certainly improved my programming - it does make you think in a different way. Check out the SICP book and videos (Scheme not LISP) - it's great.

[http://mitpress.mit.edu/sicp/](http://mitpress.mit.edu/sicp/)

(and a little script to download the SICP videos:
[https://github.com/soniah/get_sicp](https://github.com/soniah/get_sicp))
Thanks for the resources.

I'm evaluating the choices between learning Haskell vs Lisp. I used Emacs for almost a year, and I considered to learn Lisp and functional programming in general. After reading through lengthy articles and discussions, it seems to me that Lisp has many implementations, and does not have a unified standard library (for things like GUI, networking...). 

Meanwhile, Haskell is considered a purer language (based on what I read), and it seems to be more organized and less confusing.

So, can any experience Lisper tell me, what domain does Lisp serve best? Is it possible to create small scale applications, rather than large industrial project? LispWork seems really expensive for personal use. 

The Land of Lisp comic ([http://landoflisp.com/](http://landoflisp.com/)) somehow convinced me to learn Lisp (I will buy the book if I go for Lisp).

---

### Post by CptPicard on 2012-02-12
> **hoangtu said:**
> After reading through lengthy articles and discussions, it seems to me that Lisp has many implementations

SBCL is "the" implementation though... mature, stable, fast, capable.

> 
Meanwhile, Haskell is considered a purer language (based on what I read), and it seems to be more organized and less confusing.

"Pure" only in the theoretical sense of being pure-functional. That has its up- and downsides... the compiler is able to figure out much more of a "pure" program as there are never any side-effects to a function call, but it does put restrictions on the programmer.

> 
So, can any experience Lisper tell me, what domain does Lisp serve best? Is it possible to create small scale applications, rather than large industrial project?

I would say in theory it suits all domains... but not very close to the hardware kind of projects. You're much more restricted by lack of libraries than the language itself.

IMO Lisp really is a language that is worth checking out, playing with and thinkign about simply because of what it is. I have never actually used Lisp for anything substantial, but can certainly appreciate why it is appreciated by its fan base. The language itself is incredibly simple at its core, but it represents in a sense the fundamental building blocks of pretty much any other language...

---

### Post by hoangtu on 2012-02-12
> **CptPicard said:**
> 
I would say in theory it suits all domains... but not very close to the hardware kind of projects. You're much more restricted by lack of libraries than the language itself.

IMO Lisp really is a language that is worth checking out, playing with and thinkign about simply because of what it is. I have never actually used Lisp for anything substantial, but can certainly appreciate why it is appreciated by its fan base. The language itself is incredibly simple at its core, but it represents in a sense the fundamental building blocks of pretty much any other language...
Thanks. I will Learn Common Lisp, and then Clojure, since it runs on the JVM, which means I can integrate with Java. I have just had a glance at Clojure, but it seems it is a practical choice for developing web and general applications using Lisp.

---

### Post by CptPicard on 2012-02-12
You might even want to go the other way around and learn Clojure first... it's a somewhat simpler Lisp than CL in many respects, and nowadays potentially more practically useful for the reasons you stated. You get all the Lisp-mindset benefits from either one.

---


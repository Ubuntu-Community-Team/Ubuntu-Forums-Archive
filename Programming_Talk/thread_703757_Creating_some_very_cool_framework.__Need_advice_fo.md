---
title: "Creating some very cool framework.  Need advice for setting up events."
date: 2008-02-21
forum: Programming Talk
---

### Post by dempl_dempl on 2008-02-21
Hi ,

This post is partially presentation, and partially  advice-seeker :-)

 I'm currently making C++  Archiving library based on Alexandrescu's  Factory pattern.

 I'll call it ZipFactory and it'll go under GPL .
 It's completly plug-in based,   and if you, for instance, need to,  for example,  work with  **.zip**  files  you add  zipReader.cpp to your project , and call  factory to create ZipReader   .

For example , this is the  basic use:

**example.cpp **
```

#include <iostream>
#include <cstdlib>

#include <stylet/zfact/ZipReadFactory.h>
#include <stylet/zfact/components/IArchiveRead.h>


using namespace std;
using namespace zfact;





int main ( int argc, char *argv[] )
{
	cout << "\n*******************************"
		"\nZipFactory Test program"
		"\n*******************************\n\n";



		ZipReadFactory& zfact = ZipReadFactory::getInstance();
		IArchiveRead* Archive = zfact.createObject ( ".zip" );
		ZipFactoryEventReceiver EventReceiver;
		Archive->setEventReceiver(EventReceiver);
		Archive->Open("/sample-files/sample2.zip");
		
		Archive->setDestPath("$HOME/sample-files/testone/");
		Archive->Extract("*.*");
		delete Archive;


	return EXIT_SUCCESS;
}

```


Class which handles   .zip format is not included directly , it's registers itself to ZipFactory  like this :

**ZipArchiveReader.h  **:

```


class ZipArchive : public IArchive 
{
   /*  etc.... stuff ... */
}



```

**ZipArchiveReader.cpp**   

```


//*

...
implementation   of class ZipArchiveRead  ...
...
**/

//REgistration namespace .  Here's the place where   component is registrated to factory
namespace Register
{
	IArchiveRead* CreateZipRead()
	{
		return new ZipArchiveRead();
	}

	static const std::string ZIP_TYPE_ID = ".zip";

	const bool registrated = ZipReadFactory::getInstance().registerNew ( ZIP_TYPE_ID,CreateZipRead );
}


```



What's the good out of it  :


(1) Every component [archvive ] format  is decoupled from the ramework itself .  If you look carefully at    **examplefile.cpp,** you'll see that  there isn't any     statement like : 
```

#include <ZipArchiveReader.h> 

``` 
, because registration of that component is done in it's  **ZipArchiveReader.cpp** file . 
(2) That being said, you can easily figure out the way to make it all work with plugins , and to be configured at runtime. 
(3) Power,  flexibility , etc..  blah blah blah :-)  .. 



Ok.. now , here's the advice I need. 

Since we all love those progress bars, and we all like to be informed when something goes wrong, I've put some *EventReceiver* class. 

something like [ this is a retarted twin-brother of real class ]

```


class ZipFactoryEventReceiver  
{
  public:
     virtual void OnError( string what )   {}
     virtual void OnProgress( int pos, int posTotal ) {}
     
    

     /*
   .. etc ..etc
   ..
*/
}


```

When  you need to    play  with   progress bars  , you implement   the  
**ZipFactoryEventReceiver**   child class, and then you implement  the method
OnProgress. 
For example:

```

class **MyEventREceiver** : public **ZipFactoryEventReceiver** 
{
 public:
  virtual void OnProgress( int pos, int posTotal ) 
  {
     /* Some fancy progress bar code here  */
   }   
 }


```


However, there's a problem with this approach.   When you need to change one of the event handlers, you'll need to  recreate the whole new **ZipFactoryEventReceiver**'s child class.

Does anyone know better approach?  I would really hate making some crazy typelist'ed Functors, as Alexandrescu suggests :-)  .   Is there any better solution than that?

[Here's a  work in progress [ will be finished soon ]   ]("http://www.stosha.net/zipfactory01rev5.tar.bz2") .    You'll find a Kdevelop project there. You might have some problems with links, though. I'll fix that before the first release [ I'll simply going to  make my own custom makefile, instead of Kdevelop's ] . 

 

Thanks in advance

---

### Post by aks44 on 2008-02-21
Those articles about delegates in C++ may interest you:

[http://www.codeproject.com/cpp/FastDelegate.asp](http://www.codeproject.com/cpp/FastDelegate.asp) [proved by experience]
[http://www.codeproject.com/useritems/fd.asp](http://www.codeproject.com/useritems/fd.asp) [just found it, no idea of its real quality but it mentions the previous one so I assume it really is the enhancement that it claims]

:)

---

### Post by dempl_dempl on 2008-02-21
I've read the the first article too.
2nd one is the solution I've tried to avoid . It seems to crazy for me :-D 
Yeap, it seems it can't go without   Functors  : and  Template-meta programming

---

### Post by aks44 on 2008-02-21
> **dempl_dempl said:**
> 2nd one is the solution I've tried to avoid . It seems to crazy for me :-D

Well, I only read the introducing paragraph... Don Clugston's article (1st link) really is a dirty (yet working) hack... If the second article achieves the same flexibility using only *standard* C++ as it claims, it's well worth the extra complexity IMHO... ;)

---

### Post by dempl_dempl on 2008-02-21
Yeap. I always wondered how those folks in ANSI/ISO  C++ Committee   tend to overlook this kind of simple , but important things [ while creating obscene   keywords like **export**   :-)   ]

My guess is those guys never actually wrote something useful , that  they were university professors  all their  lives :-)   .  

C++ Builder has a **__closure**  keyword .   If you put it in front of a pointer to function, it can point  to a methods within different classes.   Events problem solved   . Unfortunately , I haven't used Windows in years , and all of pointers to methods in the world won't make me use it again :-D   .


Having that said, I'll  leave my Event class just the way it is, until  ANSI committee puts **closure** into standard.    **Note:**That might take a while  :-D  .   I really don't want to play with functors   .  I'm still young and I want to enjoy life as  long as I can :-D  ...

Anyway...
Thanks for your posts, Ask44!

---


---
title: "[SOLVED] Java unresolved compilation problems"
date: 2008-09-21
forum: Programming Talk
---

### Post by mlilien on 2008-09-21
I was recently working on a java project in eclipse, and tried to add a new library to the build path.  This operation crashed Eclipse, and not only that, anytime I tried to restart eclipse, it crashed.  So, I decided to uninstall and then reinstall eclipse.

Now, when I set up the program I'm working with (CMU's Sphinx) the same way that I had set up the workspace the first time, when I run an application, I get the following error:

Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
	assert cannot be resolved to a type
	Duplicate local variable rawLength
	Syntax error on token "==", = expected
	assert cannot be resolved to a type
	Duplicate local variable numStreams
	Syntax error on token "==", = expected

	at edu.cmu.sphinx.model.acoustic.TIDIGITS_8gau_13dCep_16k_40mel_130Hz_6800Hz.ModelLoader.loadDensityFileBinary(ModelLoader.java:786)
	at edu.cmu.sphinx.model.acoustic.TIDIGITS_8gau_13dCep_16k_40mel_130Hz_6800Hz.ModelLoader.loadModelFiles(ModelLoader.java:541)
	at edu.cmu.sphinx.model.acoustic.TIDIGITS_8gau_13dCep_16k_40mel_130Hz_6800Hz.ModelLoader.load(ModelLoader.java:476)
	at edu.cmu.sphinx.model.acoustic.TIDIGITS_8gau_13dCep_16k_40mel_130Hz_6800Hz.Model.allocate(Model.java:177)
	at edu.cmu.sphinx.linguist.flat.FlatLinguist.allocateAcousticModel(FlatLinguist.java:336)
	at edu.cmu.sphinx.linguist.flat.FlatLinguist.allocate(FlatLinguist.java:318)
	at edu.cmu.sphinx.decoder.search.SimpleBreadthFirstSearchManager.allocate(SimpleBreadthFirstSearchManager.java:602)
	at edu.cmu.sphinx.decoder.Decoder.allocate(Decoder.java:109)
	at edu.cmu.sphinx.recognizer.Recognizer.allocate(Recognizer.java:182)
	at demo.sphinx.hellodigits.HelloDigits.main(HelloDigits.java:52)


I didn't have this issue before reinstalling Eclipse.  Does anyone have any idea what the issue might be?  Thanks.

---

### Post by drubin on 2008-09-21
It is more then likely one of the plugins that has a bug in it.

Unless this class is your own.?
> demo.sphinx.hellodigits.HelloDigits.main(HelloDigi ts.java:52)

---

### Post by mlilien on 2008-09-21
No.  I haven't added any code.  But, it should be the same code that I got to run correctly last time.  So, I was trying to figure out if there's some kind of eclipse configuration that I wasn't using properly.

---

### Post by drubin on 2008-09-21
> **mlilien said:**
> No.  I haven't added any code.  But, it should be the same code that I got to run correctly last time.  So, I was trying to figure out if there's some kind of eclipse configuration that I wasn't using properly.

Looks like the install was not the same as the previous one. Have you tried re installing the sphinx plugin?

---

### Post by mlilien on 2008-09-21
It's not a plugin.  It's a java project.  But yes, I've tried redownloading the source and following the setup instructions several times

---

### Post by drubin on 2008-09-21
Am I right in assuming this is the [http://www.sphinxsearch.com](http://www.sphinxsearch.com)

You might get answers more specific to your issue here. I am not sure how active those forums are though. 
[http://www.sphinxsearch.com/forum/forum.html?id=1](http://www.sphinxsearch.com/forum/forum.html?id=1)

---

### Post by mlilien on 2008-09-21
Actually, what I'm using is [http://cmusphinx.sourceforge.net/sphinx4/](http://cmusphinx.sourceforge.net/sphinx4/)

I've posted on the sphinx specific message board also, but also posted here in case someone recognized the issue as something more general.  I'm pretty sure the source code hasn't changed since I reinstalled eclipse, so I don't think it's a sphinx specific issue.

---

### Post by drubin on 2008-09-21
mm Have you tried the CMD build commands to see if the issue is with the eclipse pathing/installation

---

### Post by mlilien on 2008-09-21
No, what commands are those?

---

### Post by tinny on 2008-09-21
(The usually request :-) )

Can you please post the output of:

```

java -version
javac -version

```

I have personally found that some plugins dont like some versions of the Java runtime.

rubinboy will know what im talking about ;)

---

### Post by mlilien on 2008-09-22
~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

~$ javac -version
javac 1.6.0_06

---

### Post by mlilien on 2008-09-22
I just built and ran it with ant through the command line and it worked fine.  So, I'm pretty sure it has something to do with my eclipse configuration.

---

### Post by mlilien on 2008-09-22
So, I figured out the issue.  I had to enable assertions in Eclipse.  I don't know why I didn't have to do this the first time, but it's working now.

---

### Post by drubin on 2008-09-22
> **mlilien said:**
> So, I figured out the issue.  I had to enable assertions in Eclipse.  I don't know why I didn't have to do this the first time, but it's working now.

You should report that as a bug. assertions should not affect "how" the code runs/if it causes errors/changes in code.

They are supposed to be there so that you can "view" debugging information not change the way the code reacts. This way when debugging you would get different results to the "live" version

---

### Post by mlilien on 2008-09-22
Well, before I enabled them, it seemed to be reading them as syntax errors, because it didn't see "assert" as a keyword.

---


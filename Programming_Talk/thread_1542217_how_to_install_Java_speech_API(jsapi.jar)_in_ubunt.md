---
title: "how to install Java speech API(jsapi.jar) in ubuntu 9.10"
date: 2010-07-30
forum: Programming Talk
---

### Post by Hitesh915 on 2010-07-30
hello i am using ubuntu 9.10 and i want to install java speech api. i am having the jsapi.jar file but i dont know how to provide the link between java and jsapi.jar so that my java program for speech reconization can work..! plz help me out of it . :popcorn:

---

### Post by lykeion on 2010-07-30
Have you tried adding the jar to the classpath?

See: [http://www.ibm.com/developerworks/library/j-classpath-unix/](http://www.ibm.com/developerworks/library/j-classpath-unix/)

If you use an IDE like Eclipse, see: [http://www.vogella.de/articles/Eclipse/article.html#classpath_jar](http://www.vogella.de/articles/Eclipse/article.html#classpath_jar)

---

### Post by lykeion on 2010-07-30
Since I've never used the Java Speech API I tried it out, and it wasn't so simple as you might think. These are the steps I did to make a "Hello world" example using FreeTTS.

**_[FreeTTS]("http://freetts.sourceforge.net/docs/index.php")_** is an implementation of Java Speech API. Download it **_[here]("http://sourceforge.net/projects/freetts/files/FreeTTS/FreeTTS%201.2.2/freetts-1.2.2-bin.zip/download")_**.
Unpack the archive and enter the freetts-1.2/lib subfolder.
Make the script jsapi.sh executable with:```
chmod u+x jsapi.sh
```
Then run it with:```
./jsapi.sh
```and accept the license to extract the jsapi.jar to lib subfolder.

Now you'll have a lib folder with 10 jar files. Include all of these as library jars to your project. 

I used Eclipse but the process is similar in all IDEs I guess:
Eclipse > Project > Properties 
Select Java Build Path to the left > Click Libraries tab to the right
Click button Add External Jars.. > Browse to the jar files and select them all

This is the HelloWorld example i used:
[PHP]import javax.speech.EngineList;
import javax.speech.EngineCreate;
import javax.speech.synthesis.SynthesizerModeDesc;
import javax.speech.synthesis.Synthesizer;
import com.sun.speech.freetts.jsapi.FreeTTSEngineCentral;
import java.util.Locale;

public class HelloWorld {
	public static void main(String args[]) {
		
		try {
			// create SynthesizerModeDesc that will match the FreeTTS Synthesizer
			SynthesizerModeDesc modeDesc = new SynthesizerModeDesc(
					null, 
                    "general", /* use "time" or "general" */
                    Locale.US, 
                    Boolean.FALSE,
                    null);
			if(modeDesc == null)
				System.out.println("Error creating mode descriptor");
			
			FreeTTSEngineCentral central = new FreeTTSEngineCentral();
			Synthesizer synthesizer = null;
			
            EngineList list = central.createEngineList(modeDesc);
            if (list.size() > 0) { 
                EngineCreate creator = (EngineCreate) list.get(0); 
                synthesizer = (Synthesizer) creator.createEngine(); 
            }
            
            if (synthesizer == null) {
                System.err.println("Cannot create synthesizer");
                System.exit(1);
            }
            //get ready to speak
            synthesizer.allocate();
            synthesizer.resume();

            // say hello world
            synthesizer.speakPlainText("Hello, world!", null);
            // wait until speaking is done and clean up
            synthesizer.waitEngineState(Synthesizer.QUEUE_EMPTY);
            synthesizer.deallocate();

		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}[/PHP]
For further questions about FreeTTS I suggest the **_[forum]("http://sourceforge.net/projects/freetts/forums/forum/137670")_** on their sourceforge page

---

### Post by lykeion on 2010-07-30
I noticed that you mentioned speech recognition. You should know that FreeTTS does not include this (only speech synthesis). 

On the FreeTTS they point to the **_[CMU Sphinx]("http://sourceforge.net/projects/cmusphinx/")_** project for speech recognition. They have developed various toolkits for speech recognition (incl. one for iPhone which I think is cool). 
The **_[Sphinx4]("http://cmusphinx.sourceforge.net/sphinx4/")_** project is a framework for speech recognition written in Java. Check out the **_[Programmer's Guide]("http://cmusphinx.sourceforge.net/sphinx4/doc/ProgrammersGuide.html")_** on how you would use it in your application.

---

### Post by Hitesh915 on 2010-07-31
thx for the help [lykeion]("http://ubuntuforums.org/member.php?u=102981") but i am still geting this error..!"System property "mbrola.base" is undefined.  Will not use MBROLA voices.":(

---

### Post by lykeion on 2010-07-31
> **Hitesh915 said:**
> thx for the help [lykeion]("http://ubuntuforums.org/member.php?u=102981") but i am still geting this error..!"System property "mbrola.base" is undefined.  Will not use MBROLA voices.":(

It's not an error just a warning

If you really need mbrola voices you need to set it up which is described on the FreeTTS homepage **_[here]("http://freetts.sourceforge.net/mbrola/README.html")_**. 
This includes downloading mbrola binaries and voices and setting the mbrola.base system property.
However if you don't really need mbrola voices you can ignore this warning and run with the included voices of FreeTTS.

---

### Post by Hitesh915 on 2010-07-31
hi [lykeion]("http://ubuntuforums.org/member.php?u=102981"), i used the same code of that helloworld and tried to execute it by adding all the jar files as u mentioned. but at the time of Execution it showing the warning only and i am not able to hear anything as we used the code like             synthesizer.speakPlainText("Hello world",null);
so what shuld i need to do to make this work and to listen a simple hello.
really thanx for the help lykejon..!:D

---

### Post by lykeion on 2010-08-01
Well, since you can compile and run it without any errors it should work. But just for some clarification can you specify more details, like 
* did you use the jar-files from the FreeTTS page (you've mentioned that you already had the jsapi.jar from the beginning)
* do you use an IDE like eclipse or do you run it from command-line?
* what Java JDK do you use? Sun, OpenJDK, other?
* can you describe step-by-step how you set it up, compiled and run it

But like I said, since it compiles and runs, this doesn't seem to be a Java problem, more like a general sound problem.

PS You mentioned in your first post something about "my java program for speech reconization". And now you are having troubles with a simple hello world with FreeTTS. It makes me wonder...

---

### Post by Hitesh915 on 2010-08-03
as u have shown me the way to map jsapi.jar with the Eclipse IDE. so that i used that way by adding the JAR files in Eclipse 
*so adding JAR files its done. ok
*then you wrote a simple HELLO WORLD program for an example.
*That program i copied and pasted to my Eclipse IDE included all JAR.files mentioned in the freetts.zip .

then when i try to run that program its showing me tht warning that i told you but i am not able to hear the output. "Hello World" so i think if u are able to hear that than there might b prob. with ma system..!

---

### Post by charmonie on 2011-10-08
Prefix "aoss" or "padsp" to hear the output ...

ch

---

### Post by sisco311 on 2011-10-09
Necrobumping.

Ubuntu 9.10 has reached its end of life...

Thread closed.

---


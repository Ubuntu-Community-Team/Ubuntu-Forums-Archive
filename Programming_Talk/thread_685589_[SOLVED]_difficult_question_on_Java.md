---
title: "[SOLVED] difficult question on Java"
date: 2008-02-02
forum: Programming Talk
---

### Post by xlinuks on 2008-02-02
Hi,
Can anyone help solving an issue? I'm displaying the contents of an HTML page using the (standard) class
```

javax.swing.text.html.HTMLEditorKit

```
and I need to access its images which are represented by the following (standard) class:
```

javax.swing.text.html.ImageView

```
Does anybody know how to do this? I searched a lot on this issue, there seems to be no straightforward method like HTMLEditorKit.getListOfImages();

---

### Post by Shin_Gouki2501 on 2008-02-02
i know u want a straight answer... sorry i cant provide that but if u could explain what u are trying todo a bit more in detail . I might be able to help u.

---

### Post by xlinuks on 2008-02-02
> **Shin_Gouki2501 said:**
> i know u want a straight answer... sorry i cant provide that but if u could explain what u are trying todo a bit more in detail . I might be able to help u.

Well there's a site that does translations and I'm creating an app that behaves like a browser and fetches translations for different words, it also remembers all the words "to the disk" so next time the user asks for the same words the answer comes a lot faster, there will be other enhancements as well.
For now I can save the text that Java loads into the JTextPane, but I can't save the images (the transcription characters are served as images by the server).
This is what the program looks so far:
[http://xlinuks.googlepages.com/lingvo.png](http://xlinuks.googlepages.com/lingvo.png)

Here's the program:
[http://xlinuks.googlepages.com/lingvo.zip](http://xlinuks.googlepages.com/lingvo.zip)
You should use Java 6 to run it. After unzipping the file you get the jLingvo.jar file which is the executable (which also contains the source code if you're interested helping) and a folder called "lib" which is the location where I store the saved translations and the image that is the Icon of the main frame.
The .jar file relies on the "lib" folder to be in the same directory.

---

### Post by xlinuks on 2008-02-02
thus,
to display a document of type "text/html" inside a JTextPane, Java uses the "javax.swing.text.html.HTMLEditorKit" class, which in turn uses (as I found out) the class "javax.swing.text.html.ImageView" to display the images.

---

### Post by Shin_Gouki2501 on 2008-02-02
ok i try look into that , i answer u tomorrow!

---

### Post by Shin_Gouki2501 on 2008-02-03
Ok i've checked ur Sources!
And i am somewhat gettign what you are trying to implement. Infact  i have done something similar before.

What i did was i  parsed an XHTML website to filter some of its content into an XML File.
ussing this: 

```
private void parse() throws Exception{
		URL url = new URL("http://localhost/wiki/index.php/File");            
	InputStream in = url.openStream();
	XMLInputFactory factory = XMLInputFactory.newInstance();
	XMLStreamReader parser = factory.createXMLStreamReader(in);	
	  
	//Do something with parser -> process XHTML tags... to XML-File
     while ( parser.hasNext() )
```

Same way u can access simply images from urls:
```
public UrlImageTest() throws Exception{
		URL myImageURL = new URL("http://localhost/wiki/index.gif");
		FileOutputStream fos= new FileOutputStream("index.gif");
		byte[] buffer = new byte[ 0xFFFF ]; 
		
		 for ( int len; (len = myImageURL.openStream().read(buffer)) != -1; ) 
			 fos.write( buffer, 0, len ); 
```

The Basic diffrence IMO is that u see ur read "ByteStream" as HTML WebPage while i see it as XML ( XHTML) but u should be able todo all u want with those.
So basically u need a combination of those with some serialization of the parsed content.
Should work , what u think?!

---

### Post by xlinuks on 2008-02-03
Thanks for taking the time to dive into this issue!
I solved it almost accidentally, by trying to extend the corresponding classes, and I actually got what I wanted, boy it took me so long to figure it out!
So here are the relevant classes, if interested in the whole source code see the updated links above.
HKit.java
```

package xlinuks;

import xlinuks.*;

import java.util.Vector;
import javax.swing.text.*;
import javax.swing.text.html.*;

public class HKit extends HTMLEditorKit {
	private HFactory hFactory = null;
	
	public HKit() {
		hFactory = new HFactory();
	}
	
	public ViewFactory getViewFactory() {
		return hFactory;
	}
	
	public final Vector<javax.swing.text.html.ImageView> getAllImages() {
		return hFactory.getAllImages();
	}
	
	public void clear() {
		hFactory.clear();
	}
	
}

```

HFactory.java
```

package xlinuks;

import xlinuks.*;

import java.util.*;
import javax.swing.text.*;
import javax.swing.text.html.*;

public class HFactory extends HTMLEditorKit.HTMLFactory {
	private Vector<javax.swing.text.View> vViews = null;
	
	public HFactory() {
		vViews = new Vector<javax.swing.text.View>();
	}
	
	public javax.swing.text.View create( javax.swing.text.Element elem ) {
		View view = super.create( elem );
		vViews.add( view );
		return view;
	}
	
	public void clear() {
		vViews.removeAllElements();
	}
	
	public Vector<javax.swing.text.html.ImageView> getAllImages() {
		
		int iCount = vViews.size();
		Vector<javax.swing.text.html.ImageView> vImages = new Vector<javax.swing.text.html.ImageView>();
		
		for( int i=iCount-1; i>=0; i-- ) {
			View v = vViews.get( i );
			if( v instanceof ImageView ) {
				vImages.add( (ImageView)v );
			}
		}
		
		return vImages;
	}
}

```

---

### Post by Shin_Gouki2501 on 2008-02-03
ok if your application is finished, i would like to see it :)

---

### Post by xlinuks on 2008-02-03
This issue is finished/solved, not the application, besides, as you probably noted, its meant for Russian people :)

ps: the updated version is in place of the old one [http://xlinuks.googlepages.com/lingvo.zip](http://xlinuks.googlepages.com/lingvo.zip)

---

### Post by Shin_Gouki2501 on 2008-02-03
yes i saw u take documentation from englsh, french german and itelaian documentaion and translate it locally to russian?

---

### Post by xlinuks on 2008-02-03
There's a site that does online translation from/into Russian from English, German, Italian, French and Spanish. I use(d) that page quite a lot (since my native languages are Russian and Romanian, so I sometimes have to search for (English, German) words I don't understand), but then I realized the online page is pretty unhandy, and, is missing the most obvious feature I wanted - "remembering" the words  I once asked to translate to my hard drive - so next time it takes the translation from my hard drive rather then from the internet (thus would work a lot faster). So I decided to create an app that does the same as the online page, but stores all the translated words on my hard drive. And I'm happy now. After solving the issue with images it also saves the images (transcription signs) to my hard.
It can also go to system tray and I'll implement a few other nice features that will make my friends who use(d) that online page start using my application instead! :)

The online page I'm talking about is:
[http://www.lingvo.ru/lingvo/Translate.asp](http://www.lingvo.ru/lingvo/Translate.asp)

---


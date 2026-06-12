---
title: "Custom Gedit Syntax Highlighting"
date: 2013-09-24
forum: Programming Talk
---

### Post by ryuinferno-xda on 2013-09-24
So I am trying to create a .lang file for GTK Source View:

```

<?xml version="1.0" encoding="UTF-8"?>

<language id="logcat" _name="logcat" version="2.0" _section="Others">
  <metadata>
    <property name="mimetypes">text/x-logcat</property>
    <property name="globs">*.logcat</property>
  </metadata>

  <styles>
    <style id="comment" _name="Comment"    map-to="def:comment"/>
    <style id="debug" _name="Debug" map-to="def:constant"/>
    <style id="info" _name="Info" map-to="def:string"/>
    <style id="warning" _name="Warning" map-to="def:type"/>
    <style id="error" _name="Error" map-to="def:identifier"/>
    <style id="fatal" _name="Fatal" map-to="def:error"/>
    <style id="others" _name="Others" map-to="def:string"/>
  </styles>

  <definitions>
    <context id="logcat">
      <include>
        <context id="comment" style-ref="comment">
          <start>---------</start>
          <end>$</end>
        </context>
    
        <context id="debug" style-ref="debug">
          <start>D\/</start>
          <end>$</end>
        </context>
    
        <context id="info" style-ref="info">
          <start>I\/</start>
          <end>$</end>
        </context>
    
        <context id="warning" style-ref="warning">
          <start>W\/</start>
          <end>$</end>
        </context>
    
        <context id="error" style-ref="error">
          <start>E\/</start>
          <end>$</end>
        </context>
    
        <context id="fatal" style-ref="fatal">
          <start>F\/</start>
          <end>$</end>
        </context>
    </include>>
  </definitions>
</language>

```

The sample of the file (.logcat) is as below:
```

--------- beginning of /dev/log/system 
I/auditd  (  145): Starting up 
I/Vold    (  141): Vold 2.1 (the revenge) firing up 
D/Vold    (  141): Volume sdcard0 state changing -1 (Initializing) -> 0 (No-Media) 
D/Vold    (  141): Volume sdcard1 state changing -1 (Initializing) -> 0 (No-Media) 
D/Vold    (  141): Volume usbdisk0 state changing -1 (Initializing) -> 0 (No-Media) 
--------- beginning of /dev/log/main 
I/installd(  153): installd firing up

```

And as you can see, the lines all start with "I/", "D/", "E/", "F/" or "W/", however I have read through the documentation for GTK Source View and found out that the <start> and <end> tags must contain regex expressions. So is there anyway to make it work? Thank you. :p

---

### Post by Stimpy84 on 2014-01-20
There are several things wrong with your language description file, primarily that the XML markup is broken. Perhaps you accidentally deleted a line?

In any case, I've fixed it and placed [posted it as this gist on GitHub]("https://gist.github.com/pflammertsma/8523210").

```
<?xml version="1.0" encoding="UTF-8"?>
<language id="logcat" _name="logcat" version="2.0" _section="Others">
    <metadata>
        <property name="mimetypes">text/x-logcat</property>
        <property name="globs">*.logcat</property>
    </metadata>

    <styles>
        <style id="comment" _name="Comment" map-to="def:comment"/>
        <style id="verbose" _name="Verbose" map-to="def:identifier"/>
        <style id="debug"   _name="Debug"   map-to="def:preprocessor"/>
        <style id="info"    _name="Info"    map-to="def:type"/>
        <style id="warning" _name="Warning" map-to="def:constant"/>
        <style id="error"   _name="Error"   map-to="def:keyword"/>
        <style id="fatal"   _name="Fatal"   map-to="def:error"/>
        <style id="others"  _name="Others"  map-to="def:comment"/>
    </styles>

    <definitions>
        <context id="logcat">
            <include>
                <context id="comment" style-ref="comment">
                    <start>---------</start>
                    <end>$</end>
                </context>
                <context id="datetime" style-ref="comment">
                    <start>^[0-9]</start>
                    <end>: </end>
                </context>
        
                <context id="verbose" style-ref="verbose">
                    <start>V/</start>
                    <end>$</end>
                </context>
        
                <context id="debug" style-ref="debug">
                    <start>D/</start>
                    <end>$</end>
                </context>
        
                <context id="info" style-ref="info">
                    <start>I/</start>
                    <end>$</end>
                </context>
        
                <context id="warning" style-ref="warning">
                    <start>W/</start>
                    <end>$</end>
                </context>
        
                <context id="error" style-ref="error">
                    <start>E/</start>
                    <end>$</end>
                </context>
        
                <context id="fatal" style-ref="fatal">
                    <start>F/</start>
                    <end>$</end>
                </context>
            </include>
        </context>
    </definitions>
</language>
```

If you want to make any improvements, please see the Gist on GitHub: [https://gist.github.com/pflammertsma/8523210](https://gist.github.com/pflammertsma/8523210)

---


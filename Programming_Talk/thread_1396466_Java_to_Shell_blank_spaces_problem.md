---
title: "Java to Shell blank spaces problem"
date: 2010-02-02
forum: Programming Talk
---

### Post by Ferrat on 2010-02-02
I'm using 

Runtime.getRuntime().exec(String) to use programs outside Java and it works great except for blank spaces, shell want either " " around paths containing blanks or a escape char ( \ ) to signal the break. 

In theory this should be easy using for ex. \" in the Java String or \\, however for some reason this doesn't translate well over to the Shell cause \" gets marked as a escape in shell as well and not as a containing marker and the shell reads it as just a " and \\ gets thrown over like an normal \\ escape and not one single \ as I want it to. 
And use using a single \ and forcing it to run doesn't work either :confused:

Singel ' doesn't work either

Is there anyway to get around this? 

in short is there a way to get a " or a ' or a \ translated correctly from Java to Shell?

---

### Post by Some Penguin on 2010-02-02
Might help if you can show your code that's inserting the quotes.  Off-hand, this is the sort of thing that should work.

---

### Post by Ferrat on 2010-02-02
```
 public static void main(String[] args) {
        // TODO code application logic here
        ToShell TS = new ToShell();
        String test = "mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,harddup -srate 48000 -lavcopts vcodec=mpeg2video:vpass=1:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=2500:keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 25 -o output.mpg \"/media/downloads/test movie.avi\"";
        try {
            TS.sendCMD(test);
        } catch (IOException ex) {
            Logger.getLogger(Main.class.getName()).log(Level.SEVERE, null, ex);
        }
    }
```

```
public void sendCMD(String toCMD) throws IOException{

        try {
            process = Runtime.getRuntime().exec(toCMD);
            BufferedReader bufferedReader = new
                BufferedReader(new InputStreamReader(process.getErrorStream()));
            while ((lsString = bufferedReader.readLine()) != null)
            {
                System.out.println(lsString);
            }
            try
            {
                process.waitFor();
            }
            catch (InterruptedException e)
            {
                e.printStackTrace();
            }
        }
        catch (IOException e)
        {
            e.printStackTrace();
        }
    }
```

Error returned by Mencoder is 
File not found: '[COLOR="Red"]"[/COLOR]/media/downloads/test'
Failed to open "/media/downloads/test.
Cannot open file/device.

as you can see marked red then " carries over as a escape and not as a "container marker"

---

### Post by Some Penguin on 2010-02-02
Judging from [http://java.sun.com/javase/6/docs/api/java/lang/Runtime.html](http://java.sun.com/javase/6/docs/api/java/lang/Runtime.html)

the single-string exec call invokes StringTokenizer, which is going to cheerfully chop your command into pieces based on whitespace (ignoring quotes).  It's probably not actually invoking a shell to run the process, but instead doing an exec system call.  A direct approach is breaking down the string yourself into a String[] of arguments.

---

### Post by kahumba on 2010-02-02
[Some Penguin]("http://ubuntuforums.org/member.php?u=963358") +1
This issue is actually more difficult than one would like. A few applications, at least on Linux, might only work if you send them exactly one argument, if you send more than one arg they won't pick the first one as one would expect, instead, they won't work at all (The desktop entry specification).

---

### Post by Ferrat on 2010-02-02
Well mencoder atleast works if the file name doesn't contain spaces so Iäll try chopping it up myself and see if that helps :)

EDIT:
Hmm seems spaces in filenames/paths is bad :(

---


---
title: "controlling the shell through java"
date: 2011-09-29
forum: Programming Talk
---

### Post by ubu87 on 2011-09-29
Hello guys!  

I have a question: I'm trying to know the number of columns of the terminal from java using the command **stty size** and to print the value on video, but my program doesn't work. I'll post you the code so I hope that someone will help me to find out what's going wrong.

```
import java.io.*;
import static java.lang.System.in;

public class Mah{

  public static void main(String[] args) throws IOException {


	BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
	char ch;

  ch=(char)in.read();
  if((int)ch==65) {

	try
	{
	  String[] cmd = {"/bin/sh", "-c", "/bin/stty size </dev/tty"};
	  Process p = Runtime.getRuntime().exec(cmd);
	  p.waitFor();

          System.out.print(cmd);
	}
	catch (Exception e)
	{
	   e.printStackTrace(); 
	 }


     }


}

}
```


Thanks a lot ):P

---

### Post by ofnuts on 2011-10-01
> **ubu87 said:**
> Hello guys!  

I have a question: I'm trying to know the number of columns of the terminal from java using the command **stty size** and to print the value on video, but my program doesn't work. I'll post you the code so I hope that someone will help me to find out what's going wrong.

Actually you code works (or at least you are on the right track). What works for me:
```

    public static void main(String[] args) {
        try {
            String cmd[] = { "/bin/sh","-c", "stty size </dev/tty" };
            Process p = Runtime.getRuntime().exec(cmd);

            BufferedReader cmdOut = new BufferedReader(new InputStreamReader(p.getInputStream()));
            BufferedReader cmdErr = new BufferedReader(new InputStreamReader(p.getErrorStream()));
            int rc=p.waitFor();
            System.out.println("Rc: "+rc);
            System.out.println("Command error: " + cmdErr.readLine());
            System.out.println("Command output: " + cmdOut.readLine());
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

```However... in my IDE (Eclipse): I get:
```

Rc: 2
Command error: /bin/sh: cannot open /dev/tty: No such device or address
Command output: null

```
while, in a terminal session, I get:

```

Rc: 0
Command error: null
Command output: 40 103

```

So /dev/tty may not be defined at all times.

---


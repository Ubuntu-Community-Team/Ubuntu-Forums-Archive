---
title: "execute ubuntu command from java"
date: 2012-05-07
forum: Programming Talk
---

### Post by Drenriza on 2012-05-07
Hey guys.

I have a java program where i try to execute a system command. The clear command didn't work, so just for kicks i changed it with echo

```


String command = null;
Process p = null;
int returnCode = 999;
            
/*Call linux command "clear" to clear the screen before presenting the user with a option*/
command = "/bin/echo 'test'";
            
try 
{
                p = Runtime.getRuntime().exec(command);
                System.out.println("Command executed");
} 
catch (IOException ex) 
{
                System.out.println(ex);
}
            
try 
{
                returnCode = p.waitFor();
} 
catch (InterruptedException ex) 
{
                System.out.println(ex);
}
            
System.out.println(returnCode);

```

The return code is 0 but the echo command does not get executed. Am i doing a rookie mistake anyone can point out?

Thanks on advance.
Kind regards.

---

### Post by codemaniac on 2012-05-07
Where is the start of your program execution ?
Apart from that no imports or wrapping up of code in classes .

---

### Post by Drenriza on 2012-05-07
> **codemaniac said:**
> Where is the start of your program execution ?
Apart from that no imports or wrapping up of code in classes .

What i posted is a code snipping.

The code i postet before resides in
```

public static void main(String[] args) throws ClassNotFoundException, SQLException 
    {

```

Above this my imports reside.
```

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.sql.SQLException;
import java.sql.ResultSet;

```

Kind regards.

---

### Post by codemaniac on 2012-05-07
```

BufferedReader stdInput = new BufferedReader(new 
                 InputStreamReader(p.getInputStream()));
 
BufferedReader stdError = new BufferedReader(new 
                 InputStreamReader(p.getErrorStream()));
```
Can you please append the above code snippet below .
> p = Runtime.getRuntime().exec(command);

 
So that your java program can take input from the system process .
In this case, because ypu are running the "echo" command on system, we just need to read the output of the command.

---

### Post by ofnuts on 2012-05-07
> **Drenriza said:**
> Hey guys.

I have a java program where i try to execute a system command. The clear command didn't work, so just for kicks i changed it with echo

```


String command = null;
Process p = null;
int returnCode = 999;
            
/*Call linux command "clear" to clear the screen before presenting the user with a option*/
command = "/bin/echo 'test'";
            
try 
{
                p = Runtime.getRuntime().exec(command);
                System.out.println("Command executed");
} 
catch (IOException ex) 
{
                System.out.println(ex);
}
            
try 
{
                returnCode = p.waitFor();
} 
catch (InterruptedException ex) 
{
                System.out.println(ex);
}
            
System.out.println(returnCode);

```The return code is 0 but the echo command does not get executed. Am i doing a rookie mistake anyone can point out?

Thanks on advance.
Kind regards.
"clear" is  a rather special command that may not do the same thing depending of whether stdout is a "tty" or a file/pipe. Since it's invoked from your java code its stdout may be a pipe and it may decide to not do anything. You can do the same thing by retrieving the LINES environment variable and issuing as many println().

---

### Post by Drenriza on 2012-05-07
I tried the following

```

String command = null;
            Process p = null;
            int returnCode = 999;
            
            BufferedReader stdInput = null;
            BufferedReader stdError = null;
            
            /*Call linux command "clear" to clear the screen before presenting the user with a option*/
            //command = "/usr/bin/clear";
            command = "/bin/echo 'test'";
            
            try 
            {
                p = Runtime.getRuntime().exec(command);
                
                stdInput = new BufferedReader(new InputStreamReader(p.getInputStream()));
 
                stdError = new BufferedReader(new InputStreamReader(p.getErrorStream()));
                
                System.out.println(stdInput);
                System.out.println(stdError);
                
                System.out.println("Command executed");
            } 
            catch (IOException ex) 
            {
                System.out.println(ex);
            }
            
            try 
            {
                returnCode = p.waitFor();
            } 
            catch (InterruptedException ex) 
            {
                System.out.println(ex);
            }
            
            System.out.println(returnCode);

```

The output i get is

```

xxx@xxx-CHANGEME:~/dist$ java -jar -cp lib/postgresql-9.1-902.jdbc4.jar test.jar 
java.io.BufferedReader@3ecfff
java.io.BufferedReader@1c99159
Command executed
0

```

Thanks on advance.

---

### Post by codemaniac on 2012-05-07
From the output looks like you are getting errors from the attempted command .
Can you try passing the system commandline harcoded into exec .
Also please try something that doesnot invlove single quotes .
Something like below .
 
```
p = Runtime.getRuntime().exec("ps -ef");
```

---

### Post by dwhitney67 on 2012-05-07
> **Drenriza said:**
> ...

```

System.out.println(stdInput);
System.out.println(stdError);

```

Am i doing a rookie mistake anyone can point out?


You are printing the address of the stdInput and stdError stream objects in your code.  Don't you think it might be wiser to print the contents that are within the streams?  For example:

```

String output;

while ((output = stdInput.readLine()) != null)
{
    System.out.println(output);
}

```

---

### Post by ofnuts on 2012-05-07
> **dwhitney67 said:**
> You are printing the address of the stdInput and stdError stream objects in your code.  Don't you think it might be wiser to print the contents that are within the streams?  For example:

```

String output;

while ((output = stdInput.readLine()) != null)
{
    System.out.println(output);
}

```
and that should be done in separate threads, one for each stream, otherwise your code could be waiting on stderr while there is something to read & display from stdout (and vice-versa).

---


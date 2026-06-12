---
title: "How to execute a shell command from rastertoepson filter?"
date: 2012-05-05
forum: Programming Talk
---

### Post by Gurmeet Singh on 2012-05-05
Hi,

I am working on to develope a driver for 24-pin DMP.
Firstly, I have tried to create a log file in rastertoepson filter using open function but it has not created any log file.
Then i left that one and tried to run a shell command from rastertoepson filter using popen and system function but again same result. both functions are not executing any shell command.

In normal programs like i have created a program on my system, These functions are working fine and executing shell command without any issue.

Please help me, how i can execute a shell command from raster to epson filter.
I have to get the output of shell command also.

Thanks in advance.

---

### Post by Gurmeet Singh on 2012-05-05
> Hi,

I am working on to develope a driver for 24-pin DMP.
Firstly, I have tried to create a log file in rastertoepson filter using open function but it has not created any log file.
Then i left that one and tried to run a shell command from rastertoepson  filter using popen and system function but again same result. both  functions are not executing any shell command.

In normal programs like i have created a program on my system, These  functions are working fine and executing shell command without any  issue.

Please help me, how i can execute a shell command from raster to epson filter.
I have to get the output of shell command also.

Thanks in advance.     Hello,

I have found that when i execute "/bin/date" command using Popen, it is working fine from rastertoepson filter.

In actual i want to execute "**/usr/lib/cups/backend/parallel**" command to get detail of manufacturer attached with LPT port on the system but popen is not working with this command.
I have found above mentioned command from [https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer) link to get detail of printer.

Please help me, how i can execute above command from rastertoepson filter or anyother alternative to acheive this.

Thanks..

---

### Post by Zugzwang on 2012-05-06
> **Gurmeet Singh said:**
> 
In actual i want to execute "**/usr/lib/cups/backend/parallel**" command to get detail of manufacturer attached with LPT port on the system but popen is not working with this command.


Can you elaborate on "not working" - Do you get an error message? What is the expected output? What is the output you obtain? How do you use "popen"? Do your read from the output *and* the error stream?

---

### Post by Gurmeet Singh on 2012-05-07
> Can you elaborate on "not working" - Do you get an error message? What  is the expected output? What is the output you obtain? How do you use  "popen"? Do your read from the output *and* the error stream? 	

Thanks Zugzwang for your response.

I want to get manufacturer detail from printer which has been attached on LPT port. **"/usr/lib/cups/backend/parallel**" command gives all detail of printer attached through LPT port.
My code is :
```

int CheckForMyPrinter()
{
    int MyPrinter = 0;
    FILE *fp = NULL;
      int status;
      char *cmdOut;

      /* Open the command for reading. */
      fp = popen("/usr/lib/cups/backend/parallel", "r");
        
    if (fp == NULL)
    {
         fprintf(stderr, "PAGE: Failed to run command\n");
            return 0;
      }

    /* Read the output a line at a time - output it. */
      while (fgets(cmdOut, 300, fp) != NULL) 
    {
            if(strstr(cmdOut, "MYPRINTER"))
        {
            MyPrinter = 1;
            break;
        }
      }
      /* close */
      pclose(fp);

    return MyPrinter;
}    
```

The above function always returning 0.
How i can access error stream. I am using ubuntu 11.10.

Is there any other alternative to get the manufacturer name of printer attached on LPT port. I also want to get same in serial port.

Thanks in advance.

---

### Post by Zugzwang on 2012-05-08
@OP: For debugging, add a line to print out what text you obtain from the stream.

Also, you don't distinguish between end of file and an error reading from the stream. Emit an error message in case of a failure.

---


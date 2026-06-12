---
title: "C++ - Capture output from externel exe?"
date: 2007-11-11
forum: Programming Talk
---

### Post by chrisfay on 2007-11-11
I have been researching this issue for a few days now and have devoured multple MSDN/Win32 API resources, forums etc.. without a solution. I have written a GUI based C++ application that is basically an overlay for a consle executable that I do not have access to the source code for. 

The console application iterates through a file system for certain file types and returns a count when finished. My GUI application builds out a text file and supplys it as a parameter to the executable, then kicks it off. 

My problem is capturing the output from the executable and logging it to a text file. Does anyone have code examples of how to capture standard output from a console application spawned as a process from within a C++ GUI app?

I am using CreateProcess to actually spawn the app and would love some resources on how to get this figured out....

Thanks!

---

### Post by LaRoza on 2007-11-11
I am not exactly sure what you are looking for, but:

```

ls > log.txt

```

will redirect the output of ls to a file.

Could you describe this program more? It doesn't sound all that complicated, and you could probably write one yourself.

---

### Post by chrisfay on 2007-11-11
Sure - sorry if I was unclear.

I have a console application called SubobCounter.exe that we use at work. Basically, this executable takes a text file as a parameter that specifys a location in the file system where 'subobjects' are located. (i wont go into detail as to what they are). SubobCounter.exe then chews through the file system counting how many subobjects exist and displays the total to the console window. 

I have written a C++ GUI overlay to this application that allows a user to browse for the parent directory of the subobjects and once chosen, writes out a text file with the location. This text file is then passed as the parameter to the console application SubobCounter.exe via my GUI app (using CreateProcess).

My problem is that once I spawn the SubobCounter.exe process from within my GUI app, and after its completion, I need the results written to a text file, rather than displayed to screen. In order to do this I need to grab the output from the console window. 

I can do this easily in Java or C# with a few lines of code, but in C++ it seams to be much more difficult. I have toyed with using pipes within the Windows API but can't seem to get it working.  

Here's an example in C# i found that would do this very thing:

```
private void runSyncAndGetResults_Click(object sender, System.EventArgs e)
{
 System.Diagnostics.ProcessStartInfo psi =   new System.Diagnostics.ProcessStartInfo(@"C:\listfiles.bat"); psi.RedirectStandardOutput = true; 
psi.WindowStyle = System.Diagnostics.ProcessWindowStyle.Hidden; 
psi.UseShellExecute = false; 
System.Diagnostics.Process listFiles;
 listFiles = System.Diagnostics.Process.Start(psi);
 System.IO.StreamReader myOutput = listFiles.StandardOutput;
 listFiles.WaitForExit(2000); 
[B]if (listFiles.HasExited)  {  
string output = myOutput.ReadToEnd();  
this.processResults.Text = output; 
    }[/B]}
```

Notice the part in bold - it grabs the console output from listfiles.bat and supplys it to the variable 'output'. This is essentially what I need done in order to write the output to a file.

---

### Post by chrisfay on 2007-11-11
And to be more specific, here is a snippet of thel code for the C# version of my application that kicks of the executable console app:

```
Process myProcess = new Process();

            ProcessStartInfo myProcessStartInfo = new ProcessStartInfo(currDir + "\\Resources\\SubobCounter.exe", "shadow_paths.txt");
            myProcessStartInfo.CreateNoWindow = true;
            myProcessStartInfo.UseShellExecute = false;
            myProcessStartInfo.RedirectStandardOutput = true;
            myProcess.StartInfo = myProcessStartInfo;

            //set thread/process running to true
            running = true;
            myProcess.Start();
            
            subobProc = myProcess;
             
            /[B]/get console output       
            if (!myProcess.HasExited)
            {
                StreamReader myStreamReader = myProcess.StandardOutput;
                // Read the standard output of the spawned process.
                string myString = myStreamReader.ReadToEnd();[/B]
```

Again, notice the bold portion that reads the console app's output stream.

---

### Post by NathanB on 2007-11-11
You can launch a BATCH file and have that BATCH file redirect the output to a file:

runner.bat
```

@ECHO OFF
yourprog.exe > results.txt

```

This is assuming 'yourprog.exe' outputs to STDOUT.  If, instead, it returns the desired count as an ERRORLEVEL code, then here is how to obtain that:

CreateProcess fills in the ProcessInformation structure -- one component of this is a handle to the new process (pi.hProcess).

Use WaitForSingleObject( pi.hProcess, INFINITE ) to detect when 'yourprog' is finished.

Use GetExitCodeProcess( pi.hProcess, lpExitCode ) to retrieve the wanted value.

---

### Post by chrisfay on 2007-11-11
The batch file is a good idea (the program does write to stdout), although how would I update the GUI app once it has completed?

I would like to run an undetermined progress bar while the process executes, and once it finishes, show that it has done so in the GUI. I suppose I could write something that monitors the file system for the creation of 'results.txt' file and update at that point, but not sure if that would be the best route. 

In the C# version of this application I have created a thread that executes the process - once the thread has completed it updates the gui with the results. I could be wrong, but I don't thing I could get the handle on the completion status with this method.

---

### Post by j_g on 2007-11-11
No, no. Don't do that. Win32 GUI apps have no default stdout, so you can't redirect output to a GUI app that way.

You're on the right trail. You'll use CreateProcess to launch the console app. But you'll need to create/read a pipe to capture the console app's output. Also, assuming the app allows you to pass the args on its command line, then you don't need to write out a text file containing those args. You can tell the app to read your "args" from another pipe.

You'll also want to use a STARTUPINFO struct with CreateProcess, to determine how you want the console app to run.

Here's some code below (untested -- there may be some syntax errors as I wrote it off the top of my head). You pass the name of the app to run, and also the args. It returns a buffer with the app's output. You must later free that buffer with GlobalFree(). For example, to run MyApp.exe, and have it operate upon the files "readme.txt" and "notes.txt", and receive back its output:

```
char * output;

if ((output = run_command("MyApp.exe", "readme.txt notes.txt")))
{
   MessageBox(0, output, "Success", MB_OK);
   GlobalFree(output);
}

#ifdef __cplusplus
extern "C" {
#endif

// Define OUTPUTBUFSIZE to be as big as the largest output you expect
// from the console app, plus one char. For example, if you
// expect the app to return 10 chars, define this to be 11.
#define OUTPUTBUFSIZE 4096

const TCHAR ErrorStr[] = "Error";
const TCHAR NoMem[] = "Out of memory";
const TCHAR NoPipeMsg[] = "Can't open pipe";
const TCHAR NoLaunchMsg[] = "Can't start console app";
const TCHAR NoOutput[] = "Can't read output of console app";

char * run_command(LPCTSTR cmd, LPCTSTR args)
{
STARTUPINFO sinfo;
PROCESS_INFORMATION pinfo;
SECURITY_ATTRIBUTES sattr;
HANDLE readfh, writefh;
register char *cbuff;

// Allocate a buffer to read the app's output
if (!(cbuff = (char *)GlobalAlloc(GMEM_FIXED, OUTPUTBUFSIZE)))
{
   MessageBox(0, &NoMem[0], &ErrorStr[0], MB_OK|MB_ICONEXCLAMATION);
   return 0;
}

// Initialize the STARTUPINFO struct
ZeroMemory(&sinfo, sizeof(STARTUPINFO));
sinfo.cb = sizeof(STARTUPINFO);

sinfo.dwFlags = STARTF_USESTDHANDLES | STARTF_USESHOWWINDOW;

// Uncomment this if you want to hide the other app's
// DOS window while it runs
//sinfo.wShowWindow = SW_HIDE;

sinfo.hStdInput = GetStdHandle(STD_INPUT_HANDLE);
sinfo.hStdOutput = GetStdHandle(STD_OUTPUT_HANDLE);
sinfo.hStdError = GetStdHandle(STD_ERROR_HANDLE);

// Initialize security attributes to allow the launched app to
// inherit the caller's STDOUT, STDIN, and STDERR
sattr.nLength = sizeof(SECURITY_ATTRIBUTES);
sattr.lpSecurityDescriptor = 0;
sattr.bInheritHandle = TRUE;

// Get a pipe from which we read
// output from the launched app
if (!CreatePipe(&readfh, &sinfo.hStdOutput, &sattr, 0))
{
   // Error opening the pipe
   MessageBox(0, &NoPipeMsg[0], &ErrorStr[0], MB_OK|MB_ICONEXCLAMATION);
bad1:
   GlobalFree(cbuff);
   return 0;
}

// Get a pipe to which we write the args out to the launched app
if (!CreatePipe(&sinfo.hStdInput, &writefh, &sattr, 0))
{
   // Error opening the pipe
   MessageBox(0, &NoPipeMsg[0], &ErrorStr[0], MB_OK|MB_ICONEXCLAMATION);
bad2:
   CloseHandle(readfh);
   CloseHandle(sinfo.hStdOutput);
   goto bad1;
}

// Launch the app. We should return immediately (while the app is running)
if (!CreateProcess(0, cmd, 0, 0, TRUE, 0, 0, 0, &sinfo, &pinfo))
{
   MessageBox(0, &NoLaunchMsg[0], &ErrorStr[0], MB_OK|MB_ICONEXCLAMATION);
   CloseHandle(sinfo.hStdInput);
   CloseHandle(writefh);
   goto bad2;
}

// Don't need the read access to these pipes
CloseHandle(sinfo.hStdInput);
CloseHandle(sinfo.hStdOutput);

// We haven't yet read app's output
sinfo.dwFlags = 0;

// Input and/or output still needs to be done?
while (args || readfh)
{
   // More args to the app?
   if (args)
   {
      if (!(*args))
      {
         // Ok, we're done writing out the args to the app.
         // We can close that pipe now, and clear 'args' so
         // that we stop writing out args
         CloseHandle(writefh);
         writefh = args = 0;
      }

      // Write out more args to the app
      else
      {
         if (!WriteFile(writefh, args, lstrlen(args), &pinfo.dwThreadId, 0))
         {
bad4:  GlobalFree(cbuff);
            cbuff = 0;
            break;
         }

         args += pinfo.dwThreadId;
      }
   }

   // Capture more output of the app?
   if (readfh)
   {
      // Read in upto OUTPUTBUFSIZE bytes
      if (!ReadFile(readfh, cbuff + sinfo.dwFlags, OUTPUTBUFSIZE - sinfo.dwFlags, &pinfo.dwProcessId, 0) || !pinfo.dwProcessId)
      {
         // If we aborted for any reason other than that the
         // app has closed that pipe, it's an
         // error. Otherwise, the program has finished its
         // output apparently
         if (GetLastError() != ERROR_BROKEN_PIPE && pinfo.dwProcessId)
         {
            // An error reading the pipe
            MessageBox(0, &NoOutput[0], &ErrorStr[0], MB_OK|MB_ICONEXCLAMATION);
            goto bad4;
         }

        // Close the pipe
         CloseHandle(readfh);
         readfh = 0;
      }

      sinfo.dwFlags += pinfo.dwProcessId;
   }
}

// Close input pipe if it's still open
if (writefh) CloseHandle(writefh);

// Close output pipe
if (readfh) CloseHandle(readfh);

// Wait for the app to finish
WaitForSingleObject(pinfo.hProcess, INFINITE);

// Close process and thread handles
CloseHandle(pinfo.hProcess);
CloseHandle(pinfo.hThread);

// Nul-terminate it
if (cbuff) *(cbuff + sinfo.dwFlags) = 0;

// Return the output
return cbuff;
}

#ifdef __cplusplus
}
#endif

```

P.S. Why on earth are you asking Windows programming questions on a Linux distro's forum? You'd best go to a Windows programming newsgroup, or someplace like Code Project.

---

### Post by chrisfay on 2007-11-12
Fantastic!!!

With a little modification that did exactly what I needed to do. The text file parameter is required by the executable (tried using paths as arguments and it specifically looks for a text file), so removing that portion and manually specifying the command and text file in the createprocess worked great.

Thank you so much!

p.s. - I posted my question in this forum because I've had great success getting help for a wide variety of issues here. I felt it a good place to start getting feedback since there are some very talented people on this forum - thanks again, i was about to head bang my monitor.

---

### Post by j_g on 2007-11-12
> **chrisfay said:**
> With a little modification that did exactly what I needed to do.

Glad to hear that.

> there are some very talented people on this forum.

Perhaps so, but obviously they will be Linux programmers, and Win32 can do things quite differently than Linux. For example, the obvious Linux solutions of redirecting stdout via the command line (whether specified directly, or in a batch file) do not work in this context. Your best bets are Code Project, MSDN (don't know why your search didn't turn up something -- I think I got some of the info for my above code from there), and a windows programming newsgroup such as comp.os.ms-windows.programmer.win32, as these are where most Windows programmers go for info. In fact, if you ask in that Win32 newsgroup, and MSDN has the answer for you, someone will likely give you the precise MSDN URL.

---

### Post by chrisfay on 2007-11-18
Another question - 

What's the best method to resize the output buffer dynamically if it fills up?

Some of the commands I'm running return beyond the 4096 character buffer defined. I can increase them manually, but how do I do this within the application dynamically?

When this happens, the app simply freezes, rather than returning an error as the code emplys it should (at least it seems). 

Thanks

---

### Post by j_g on 2007-11-18
In my preceding example, I did a #define to set OUTPUTBUFSIZE to the maximum size I expected my buffer ever needed to be. And that buffer was allocated as so.

By "manual" adjustment, I assume you mean just setting OUTPUTBUFSIZE to a bigger value, and recompiling your code.

I presume what you want to do instead is resize the buffer within the loop where you read the program's output. So even if OUTPUTBUFSIZE is not big enough, your software can still account for this.

Well, one thing you can do is add some logic to your loop where, if you completely fill the buffer, then you can allocate a second buffer of a bigger size (ie, maybe add OUTPUTBUFSIZE to the current size of the original buffer). You copy the contents of the old buffer to this new, larger buffer. Then you free the first buffer, and start using the second buffer instead. You'd need to have a variable that holds the current size of the buffer. We'll call that "cbuffSize".

So when you initially allocate cbuff, you set cbuffSize to that initial size:

```
register char *cbuff;
register unsigned int cbuffSize;

cbuff = (char *)GlobalAlloc(GMEM_FIXED, OUTPUTBUFSIZE);
cbuffSize = OUTPUTBUFSIZE;
```

Now later in your loop, you need to always check the size of cbuff, to determine when it is filled. If filled, then you allocate a second buffer of the size cbuffSize + OUTPUTBUFSIZE. You copy cbuff to this new buffer. Then you free cbuff. Finally you set the variable cbuff to point to this new buffer.

```
if (readfh)
{
   // Have we filled cbuff?
   if (sinfo.dwFlags >= cbuffSize)
   {
      register char *temp;

       // We filled it. We need to get a larger buffer
       if (!(temp = (char *)GlobalAlloc(GMEM_FIXED, cbuffSize + OUTPUTBUFSIZE)))
      {
         MessageBox(0, &NoMem[0], &ErrorStr[0], MB_OK|MB_ICONEXCLAMATION);
         goto bad4;
      }

      // Copy the old buffer to the new buffer
      CopyMemory(temp, cbuff, cbuffSize);

      // Now set cbuffSize to this new, larger size
      cbuffSize += OUTPUTBUFSIZE;

      // We don't need the old buffer
      GlobalFree(cbuff);

      // Set cbuff to the new buffer
      cbuff = temp;
   }

   // Read in as many bytes as we have room for
   ReadFile(readfh, cbuff + sinfo.dwFlags, cbuffSize - sinfo.dwFlags, &pinfo.dwProcessId, 0);

//.... etc. The rest of the loop is the same as before
```

The above is easy to do. But it results in needing to have a second buffer (which could put more pressure on system RAM).

What you may prefer to do is "reserve" a really, really large buffer of "virtual memory". This an area of memory that the system "reserves" for your use, but doesn't actually give you yet. Then, you can tell Windows to actually give you another piece as you need it (where each piece is typically 4096 bytes -- referred to as a "page"). It's very similiar code to the above, but you use VirtualAlloc instead of GlobalAlloc (and VirtualFree instead of GlobalFree).

The advantage of VirtualAlloc is that, you only use one buffer, so it can be less memory intensive than two buffers. Plus it can be faster because you don't have to copy between two buffers periodically. The disadvantage is that your process has a finite amount of virtual memory available to it. And if you reserve a really, really large bit of it, and then hold onto it for a long time, it's possible that your subsequent calls to GlobalAlloc/malloc/VirtualAlloc could fail (more easily than if you just used GlobalAlloc). But if you're going to use that VirtualAlloc'ed buffer for a short time, and then VirtualFree it (before many subsequent calls to allocate even more memory), then there's no need for any concern. What I'm saying is that you can't reserve lots and lots and lots of virtual memory, hold onto that memory, and still expect to be able to allocate even more memory beyond that.

So here is how you use VirtualAlloc:

```
// I'm going to specify a really, really big buffer. More
// than I'll _ever_ need _for sure_. 131,072 bytes. If you set
// this to a different value, keep it a multiple of
// 4096 (ie, the size of a single page)
#define OUTPUTBUFSIZE (4096 * 32)

// Ask the OS to reserve upto 131,072 bytes for our
// buffer. We haven't actually allocated even a single
// byte yet. We've only reserved that much mem
if (!(cbuff = (char *)VirtualAlloc(0, OUTPUTBUFSIZE, MEM_RESERVE, PAGE_READWRITE)))
{
   MessageBox(0, &NoMem[0], &ErrorStr[0], MB_OK|MB_ICONEXCLAMATION););
   return 0;
}

// Although we've asked the OS to reserve 131,072 bytes, we haven't yet
// told the OS to actually give us access to any bytes of it
cbuffSize = 0;
```

And in the loop:

```
if (readfh)
{
   // Have we filled cbuff?
   if (sinfo.dwFlags >= cbuffSize)
   {
      register char *temp;

       // We filled it. We need to tell the OS to give us access to another piece
       // (ie, another 4096 bytes) of our reserved memory
       if (!(temp = (char *)VirtualAlloc(cbuff, cbuffSize + 4096, MEM_COMMIT, PAGE_READWRITE)))
      {
         MessageBox(0, &NoMem[0], &ErrorStr[0], MB_OK|MB_ICONEXCLAMATION);
         goto bad4;
      }
      cbuff = temp;

      // Now set cbuffSize to this new, larger size
      cbuffSize += 4096;
   }

   // Read in as many bytes as we have room for
   ReadFile(readfh, cbuff + sinfo.dwFlags, cbuffSize - sinfo.dwFlags, &pinfo.dwProcessId, 0);

//.... etc. The rest of the loop is the same as before, except use
// VirtualFree instead of GlobalFree
```

NOTE: If you use Virtual memory, you have to eventually free the buffer with a call to:

```
VirtualFree(cbuff, 0, MEM_RELEASE);
```

Do not try to free virtual memory with GlobalFree() nor free()! You must use VirtualFree to free a piece of virtual memory. In fact, change any calls from GlobalFree to VirtualFree (as shown in the above line) in my previous example code, if you decide to go with virtual memory.

P.S. In my original code I gave you, I accidentally had a call to VirtualFree() there, when it should have been GlobalAlloc(). That could have accounted for that "freeze". You can't free GlobalAlloc'ed memory with VirtualFree either. I've corrected my previous post.

---

### Post by chrisfay on 2007-11-18
Thank you so much for your detailed response and help - this is exactly what I was looking for. 

Do you have any good recommendations for online resources that cover this material? I would love to better understand everything that is going on here.

---


---
title: "Return variable from thread in c++"
date: 2011-09-27
forum: Programming Talk
---

### Post by Rich78 on 2011-09-27
Hi,

Sorry that this relates to a Windows dev issue but I'm hoping you'll all look past that bit :).

I'm working on a dll in c++ and I've had to wrap the functionality within a thread as it was complaining when I called the COM Initialize as it was already open (dll is being called from C#), and I'm basically just wrapping up some existing code from the vshadow sample in the Windows api.

I'm calling the following code:

hdl = CreateThread(NULL, 0, mainThread, (LPVOID)&p, 0, NULL);
	if (hdl == NULL)
		ExitProcess(Data_Of_mainThread);
	WaitForSingleObject(hdl,INFINITE);
	CloseHandle(hdl);

DWORD WINAPI mainThread(LPVOID lpParam)
{
   //Thread code blah blah blah
}

As you can see mainThread has a return of DWORD, which I'm led to believe is basically an unsigned int.  

I'm wanting to return a GUID from the code within mainThread back to the code that executed the CreateThread method.

All is in the same class.

Thanks for any help.

---

### Post by Tony Flury on 2011-09-27
The only way I can think of is to change the API of your function so that you pass it a shared memory area i.e. a class instance, or similar, and your function stores it's return into that memory.

From what i know of threads is that they have no return value.

---

### Post by Rich78 on 2011-09-27
Thanks for this, I was coming to that conclusion but just wanted to make sure I wasn't being dumb as there seems little on the topic other than being able to retrieve the exit code, which is basically the unsigned int.

Is there a nasty way to do it such as a public static variable or something or would the thread have no access to it?

I'm fairly new to C++ so I'm bumbling my way through it :).

---

### Post by Rich78 on 2011-09-27
Finally fixed it!!

Instead of creating my own thread wrapped around the COM code, I changed the COM Initializer from

CoInitialize(NULL)

To

CoInitializeEx(NULL, COINIT_MULTITHREADED)

This allowed me to pass values back as normal as no functionality was wrapped in a thread.

---


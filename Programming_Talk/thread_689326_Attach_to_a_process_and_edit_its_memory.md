---
title: "Attach to a process and edit its memory"
date: 2008-02-06
forum: Programming Talk
---

### Post by ensis2k on 2008-02-06
Hello,

I am trying to read the memory of another process with C++ to make a memory hacking tool (cheat engine etc.)

Here my approach:
1. attach to process
2. open /proc/PID/mem with fstream
3. search its content for some value
4. detach from process
5. change something inside the monitored process
6. attach
7. compare found memory regions with the anticipated value

Problem is that the memory does not seem to change even though the monitored process changes.

The adress range i search for values is [0x00400000,0x7FFFFFFF]

Here is a summary of my code wich only reads values:

```

#define HEAPSTART (0x00400000)
#define HEAPEND   (0x7FFFFFFF)

  ptrace(PTRACE_ATTACH, pid, NULL, NULL);
  wait(NULL);	

  ifstream myfile;
  myfile.open (filename, /*ios::out |*/ ios::in | ios::binary);
	
  if (myfile.is_open()) {
    size_t pos;
    
    myfile.seekg(HEAPSTART);
		
    if(searchModeNew) { // new search
      while ((!myfile.eof()) && ((pos = myfile.tellg()) < HEAPEND))    
      {    	
        myfile.read ((char*)&var, sizeof(var));
	      
	if(var == value) {
	  valueFound(pos);
	  ctr++;
	}
	      
	myfile.seekg(pos + 1);
      }
    } else { //consecutive search

      map<size_t, search_t>::iterator iter;
	 
        for(iter = values.begin(); iter != values.end(); iter++)
	{
	  myfile.seekg(iter->first);
	  myfile.read ((char*)&var, sizeof(var));
	  if(var == value) {
	    valueFound(pos);
	    ctr++;
	  } else {	    
	    removeAdress(pos);
	  }      
	}			
    }				
    
    cout << "Value was found " << ctr << " times." << endl;
    cout << "List size is " << values.size() << "." << endl;
    myfile.close();		
    ptrace(PTRACE_DETACH, pid, NULL, NULL);		

```


Thank you for reading my concern

---


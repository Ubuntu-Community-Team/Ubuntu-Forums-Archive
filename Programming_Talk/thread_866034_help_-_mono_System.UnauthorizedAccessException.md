---
title: "help - mono: System.UnauthorizedAccessException:"
date: 2008-07-21
forum: Programming Talk
---

### Post by jreis on 2008-07-21
[FONT=Verdana][SIZE=2][SIZE=2][SIZE=2]Hello, 
  
 I'm new to c# and mono, and i need some help to solve a problem 
  
I have develop something like a simple wget application, with some features that i needed, to run on windows and on *nix machines. 
  
 All went well until i started to download the files to the local PC. The error (both on windows and linux machines) is:
[/SIZE][/SIZE][/SIZE][/FONT]```
[FONT=Verdana][SIZE=2][SIZE=2][SIZE=2][FONT=Courier New][SIZE=1]System.UnauthorizedAccessException: Access to the path '/home/jose/desktop/teste' is denied. 
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000]  
   at System.IO.FileStream..ctor (System.String path, FileMode mode) [0x00000]  
   at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode) 
   at System.Net.WebClient.DownloadFileCore (System.Uri address, System.String fileName) [0x00000]  
   at System.Net.WebClient.DownloadFile (System.Uri address, System.String fileName) [0x00000]  
   at System.Net.WebClient.DownloadFile (System.String address, System.String fileName) [0x00000]  
   at (wrapper remoting-invoke-with-check) System.Net.WebClient:DownloadFile (string,string) 
   at getter.MainClass.Main (System.String[] args) [0x00000] [/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/FONT][SIZE=2]
[/SIZE]
```[SIZE=2]

[/SIZE][FONT=Verdana][SIZE=2][SIZE=2][SIZE=2]I have already gave full permissions to everyone in the local folder. Can some one suggest some way to solve this problem, i'm getting desperate! 
  
 the code that i'm using is: [/SIZE][/SIZE][/SIZE][/FONT][SIZE=2]
[/SIZE]```
[FONT=Verdana][SIZE=2][SIZE=2][SIZE=2][FONT=Courier New][SIZE=1]string loc="/home/jose/desktop/teste"; 
for (int i = 0; i < (result.Length-1); i++){ 
string [] subresult = result[i].Split(new Char[] {';'}); 
  Console.WriteLine("File to get his :: {0} and His MD5 is:: {1}\n", subresult[0], subresult[1]); 
  try{
    System.Net.WebClient client = new WebClient(); 
    client.DownloadFile(subresult[0], loc); 
  }
  catch(Exception e) 
  { 
   Console.WriteLine(e.ToString()); 
  }
}[/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/FONT][SIZE=2]
[/SIZE]
```[SIZE=2]
[/SIZE]

---


---
title: "Problem with uploading a file on Ubuntu"
date: 2011-03-04
forum: Programming Talk
---

### Post by usmanajmal on 2011-03-04
I have developed a Flex+PHP based application in which  there is a functionality to  upload a picture to the server. **The  application uploads a picture fine  if run on Windows or OpenSuSE.** But on Ubuntu,  file is not getting  upload at all.
 
Here is the log I maintain while uploading a file:
 
Uploading 5408_1243356204478_1246540615_30751024_3730562_n.jpg...
File opened
File upload in progress (349 of 31340)
File upload in progress (349 of 31340)
File upload in progress (31340 of 31340)
File upload in progress (31340 of 31340)
File upload in progress (31340 of 31340)
File upload in progress (31340 of 31340)
File upload in progress (31340 of 31340)
File upload in progress (31340 of 31340)
File upload in progress (31340 of 31340)
File upload in progress (31340 of 31340)
HTTP error occured - 
HTTP IO error occured - 

I have set the tmp directory in php.ini to /tmp whose permission are set to 777.
Also, I have set the allowable upload file size in php.ini to 40 MB for the time being.

Any clue what's going wrong?

---

### Post by An Sanct on 2011-03-04
And the image is then copied from the temporary folder to another location right?  Who is the scripts "owner" and what permissions are on that folder?

---

### Post by usmanajmal on 2011-03-04
Thanks for replying. :) Yes. But I can't see it even in the /tmp.

/tmp 
Permissions: 777
Owner: root

/var/www/bin-release/ (This is where the image should go finally)
Permissions: 777
Owner: root

---

### Post by An Sanct on 2011-03-04
And the php script? Has it got permissions to write/modify, who is the owner?

Its a security breach to have root owned scripts in your /var/www :)

PS.
a quick qoute from [another forum]("http://forum.mamboserver.com/showthread.php?t=90437")

> Anyway, 777 = rwxrwxrwx ? Isn't that insecure?
I usually set my permissions as follows:
owner,group = apache,apache
files,directories = -rw-r--r--,drwxr-xr-x

So mainly there are permission problems, are you in the www-data group?

---

### Post by usmanajmal on 2011-03-04
Yeah you are right about the insecure thing. :)

Okay I have now set permissions of /var/www/bin-release/* as:

owner,group = usman,www-data
files,directories = 777,777

I have also added usman to the www-data group in /etc/group

The problem is still there though... :(

PS
The php script is residing in bin-release/ so it has same permissions as mentioned above

---

### Post by An Sanct on 2011-03-04
On my server I have a script, that allows uploads, its permissions are 644 (so owner everything, others read only)

In my script tho, if the file is a binary (possible attack) it will be deleted automatically, so move from tmp to null and not to the target folder.

Who wrote the script? Is it public or your own work?

---

### Post by usmanajmal on 2011-03-04
It's public. Here it is

**ActionScript:**
```
//--------------------------------------------File Uploading------------------------------------------------ 
             
            // We declare the file reference here so it is not destroyed by memory garbage collection. 
            public var fileRef:FileReference = new FileReference(); 
            // a class that is similar to a HTML form 
            public var request:URLRequest; 
            public var uploadFile:String = "upload.php"; 
             
            // Following opens a browser window for the user to select a file to upload 
            public function upload():void { 
                // Listen for the upload events 
                // http://livedocs.adobe.com/flex/3/html/17_Networking_and_communications_7.html 
                fileRef.addEventListener(Event.SELECT, selectHandler); 
                fileRef.addEventListener(Event.OPEN, openHandler); 
                fileRef.addEventListener(ProgressEvent.PROGRESS, progressHandler); 
                fileRef.addEventListener(Event.COMPLETE, completeHandler); 
                fileRef.addEventListener(DataEvent.UPLOAD_COMPLETE_DATA, uploadCompleteHandler); 
                fileRef.addEventListener(SecurityErrorEvent.SECURITY_ERROR, httpSecurityErrorHandler); 
                fileRef.addEventListener(HTTPStatusEvent.HTTP_STATUS, httpErrorHandler); 
                fileRef.addEventListener(IOErrorEvent.IO_ERROR, httpIOErrorHandler); 
                 
                // browse for the file to upload 
                // when user selects a file the select handler is called 
                try { 
                    var success:Boolean = fileRef.browse(); 
                } 
                catch (error:Error) { 
                    trace("Unable to browse for files."); 
                    testTextArea.appendText("Unable to browse for files."); 
                } 
            } 
             
            // Following checks that the upload PHP file is where we think it is 
            public function test():void { 
                request = new URLRequest(uploadFile); 
                navigateToURL(request,"_blank"); 
            } 
             
            // When a file is selected, we upload the file to the PHP file upload script on the server 
            public function selectHandler(event:Event):void { 
                request = new URLRequest(uploadFile); 
                try { 
                    // upload file 
                    fileRef.upload(request); 
                    testTextArea.appendText("Uploading " + fileRef.name + "..."); 
                } 
                catch (error:Error) { 
                    // vague 
                    trace("Unable to upload file."); 
                    testTextArea.appendText("\nUnable to upload file."); 
                } 
            } 
             
            // Following dispatched during file open.  
            public function openHandler(event:Event):void { 
                trace("File opened"); 
                testTextArea.appendText("\nFile opened"); 
            } 
             
            // Following dispatched during file upload 
            public function progressHandler(eventprogressEvent):void { 
                trace("File upload in progress (" + event.bytesLoaded + " of " + event.bytesTotal + ")"); 
                testTextArea.appendText("\nFile upload in progress (" + event.bytesLoaded + " of " + event.bytesTotal + ")"); 
            } 
             
            // Following dispatched when the file has been given to the server script 
            // this event does not receive a response from the server 
            // use DataEvent.UPLOAD_COMPLETE_DATA event as shown in uploadCompleteHandler 
            public function completeHandler(event:Event):void { 
                trace("File uploaded"); 
                testTextArea.appendText("\nDONE"); 
                uploadTextInput.text = fileRef.name; 
            } 
             
            // Following dispatched when a file upload has completed 
            // this event can contain a response from the server as opposed to the Event.COMPLETE event 
            // the PHP upload file can send back information if we want it to 
            // the event.data and event.text properties would contain a response if any 
            public function uploadCompleteHandler(event.dataEvent):void { 
                trace("Information about upload: \n" + String(event.text)); 
                //textarea1.text += "\nInformation about upload \n" + event.text as String; 
            } 
             
            // Following dispatched when an http error occurs 
             
            // 404 is can't find file 
            // test the file exists 
            public function httpErrorHandler(event:HTTPStatusEvent):void { 
                trace("HTTP error occured " + event.status); 
                testTextArea.appendText("\nHTTP error occured - "); 
            } 
             
            // Following dispatched when an http io error occurs 
             
            // Error #2038: File I/O Error. - can't find the PHP file 
            // DO THE FOLLOWING: 
            // - check that the file name is spelled correctly in the uploadFile variable 
            // - check that the path to the file is correct (click test file exists button) 
            // - make sure you are running a PHP server locally (google search for MAMP or XAMPP) 
            // - make sure you are publishing to your PHP server 
            // - make sure you are pointing to the correct path in your local server (preferences > document root) 
            // - manually check the file is on your server 
            public function httpIOErrorHandler(event:IOErrorEvent):void { 
                trace("HTTP IO error occured - " + event.text); 
                testTextArea.appendText("\nHTTP IO error occured - "); 
            } 
             
            // Following dispatched when an http io error occurs 
             
            // Error #2049: Security sandbox violation means  
            // your &#8216;.swf' and PHP file are on different servers or directories 
            // make sure the PHP file is in the same or a subdirectory 
            // or add a cross domain security file to the same directory where the PHP file is 
            // check / for the latest documentation on cross domain policy files 
            public function httpSecurityErrorHandler(event:SecurityErrorEvent):void { 
                trace("HTTP Security error occured - " + event.text); 
                testTextArea.appendText("\nHTTP Security error occured - "); 
            } 
            //-------------------------------------File Uploading-End-------------------------------------------
```**upload.php**
[PHP]<?php 
$target = "./"; 
$target = $target . basename( $_FILES['Filedata']['name']) ; 
$ok=1; 
  
try 
{ 
    move_uploaded_file($_FILES['Filedata']['tmp_name'], $target) or die("Can't upload file");; 
    echo "The file ". basename( $_FILES['Filedata']['name']). " has been uploaded"; 
    $stringData = " uploaded: "; 
} 
catch(Exception $e) 
  { 
      echo "The exception message follows\n"; 
      echo 'Message: ' .$e->getMessage(); 
  } 
?> [/PHP]

---


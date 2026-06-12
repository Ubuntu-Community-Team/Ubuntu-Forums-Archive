---
title: "Php output error."
date: 2009-05-11
forum: Programming Talk
---

### Post by dragos240 on 2009-05-11
I was uploading an upload script to my website, for a simple desktop upload site much like ourdesktops.com, oddly, it just displays the contents of the file: Here is the file:
```

$target_path = "";

$target_path = $target_path . basename( $_FILES['uploadedfile']['name']);

if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
    echo "The file ".  basename( $_FILES['uploadedfile']['name']).
    " has been uploaded";
} else{
    echo "There was an error uploading the file, please try again!";
}


```

---

### Post by jinksys on 2009-05-11
Is the script in proper form?  
By that I mean, 
do you use <?php ?>

Is the script have the php extension?

Do you have PHP installed?

---

### Post by Reiger on 2009-05-11
Just for reference: you should really check the size of the upload as well as the 'error' code (should be UPLOAD_ERR_OK).

---

### Post by dragos240 on 2009-05-12
> **jinksys said:**
> Is the script in proper form?  
By that I mean, 
do you use <?php ?>

Is the script have the php extension?

Do you have PHP installed?

I recall using that,

I have a php extention

Hai, I do.

---

### Post by hessiess on 2009-05-12
So the PHP code displays in the browser?, do any outher PHP scripts work? If you are using a local server are you browsing to the file with the webserver, i.e. [http://localhost/phpscript.php](http://localhost/phpscript.php). Just doubbleckicking on the file won't work. 

You do know that that script is exreamly inscure and could be used to upload PHP scripts(MASSIVE sccurity hole), or anything basically.

---

### Post by dragos240 on 2009-05-12
Yes, I am sure, I have 2 files for the uploader, upload.php and uploader.php. Upload.php works, and I have a simple machine forum, it works great. I'm just not sure whats happening now.

EDIT: I have a 2mb limit, and it only uploads to a certain directory, this is in upload.php, uploader.php is the one I posted as it doesn't work. If you want me to post upload.php, I will.

---


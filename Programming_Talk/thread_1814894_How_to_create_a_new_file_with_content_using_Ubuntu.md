---
title: "How to create a new file with content using Ubuntu One API and PHP"
date: 2011-07-30
forum: Programming Talk
---

### Post by paglia96 on 2011-07-30
I'm having some problems when i try to create a new file with some content (or overwrite the content of an existing one) using Ubuntu One API and PHP.

I can easily create and empty file or folder using:

PUT /api/file_storage/v1/~/path/to/volume/path/to/node

but i don't understand ho to use this specification:

> PUT /api/file_storage/v1/ + <directory.content_path> + '/' + filename.ext, or /api/file_storage/v1/ + <file.content_path>

PUT a new file, with content, in one action, or overwrite content of an existing file.
The body of the PUT request is the content of the file.
Note that you cannot PUT a new file with content and alter its attributes at the same time.
Note also that content_paths may not be rooted under the API root, and may change without warning, so they must be read from the API and not hardcoded.
(Note caveat above about CONTENT_ROOT being temporarily different.)
I don't post the whole code but only the line which doesn't work:


[PHP]$api_url = 'https://one.ubuntu.com/api/file_storage/v1/'; 
$filecontent = "content of the txt file"; 

$oauth->fetch($api_url.'~/UbuntuOne/try.txt', $filecontent, OAUTH_HTTP_METHOD_PUT);  [/PHP]
I don't understand how to structure the syntax. Can you help me?
    	
I've yet posted this in the Ubuntu One section but i think that this is more appropriate

---


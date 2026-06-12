---
title: "image uploader, uploads but still gives error"
date: 2009-07-27
forum: Programming Talk
---

### Post by ELD on 2009-07-27
Basically my image upload seems to work fine, it uploads the image in question ive tested that a few times, but it seems to then return with a blank error message.

Here is my code:
[php]
function upload_item($item_id) 
{ 
    global $site_config, $db_pxs, $lang, $pxs, $error; 
     
    $error = ''; 
     
    // first we check if it is allowed 
    $allowed_extensions = array('image/jpeg'); 
             
    if (in_array($_FILES['new_upload']['type'], $allowed_extensions)) 
    { 
        // check file size not bigger than 1.47mb 
        if ($_FILES['new_upload']['size'] > 1542000) 
        { 
            $error = 'Sorry file is too big!'; 
            return false;     
        } 
     
        // THE MAIN FILE 
        // give the file a random file name 
        $filename = rand() . 'id' . $item_id . $_FILES['new_upload']['name']; 
                 
        // the actual file 
        $source = $_FILES['new_upload']['tmp_name']; 
                 
        // where to upload to 
        $target = "uploads/" . $filename; 
        // 
                 
        if (move_uploaded_file($source, $target)) 
        { 
            return $filename; 
        } 
             
        else 
        { 
            $error = 'Could not upload file, please contact the admin!'; 
            return false;     
        } 
    } 
     
    else 
    { 
        $error = 'Wrong file type, allowed to upload .jpg files only.'; 
        return false;     
    } 
}
[/php]
The image appears in my upload directory fine.
I don't see why it gives a blank error, i set only 3 error messages possible?
Here is the checking code:
[php]
    // initial screenshot 
    if ($_FILES['new_upload']['error'] == UPLOAD_ERR_OK) 
    { 
        if (upload_item($db_pxs->last_id()) == false) 
        { 
            $pxs->admin_error($error); 
        }

        $screenshot_sql = "INSERT INTO `item_screenshots` SET `item_id` = {$db_pxs->last_id()}, `image` = '{$filename}'"; 
        $query_shot = $db_pxs->query($screenshot_sql); 
    }
[/php]

It doesn't seem to get to the screenshot sql, giving a blank error message above :(, yet it does upload the file :S

Any help would be great!

---


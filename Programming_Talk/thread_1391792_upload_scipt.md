---
title: "upload scipt"
date: 2010-01-27
forum: Programming Talk
---

### Post by razzer on 2010-01-27
Hello, im having a problem with my upload script as i pasted bellow. if you go to [http://ashenvale.se/testing/](http://ashenvale.se/testing/) you will se it in action. please try to upload someting as it wont work and there is no error. the /testing/ folder is chmoded 777 aswell as the file. what would this problem be ? :/

[PHP]<?

class Upload {
    
    ## User edited variables ##
    
    public $upload_dir = '/var/www/testing/'; // Name of the upload directory - create it yourself and chmod it to 777
    public $deletable = true; // Are files deletable ? true or false
    public $file_extensions  = array('.zip','.jpg','jpeg','.png','.gif','.doc'); // File extensions allowed to be uploaded
    public $max_size = 200000000; // Maximum file size
    
    ## Stop editing passed this point unless you know what you are doing ##
    
    function index() {
        if (isset($_REQUEST['delete'])) {
            $this->delete($_REQUEST['delete']);
        }
        if (isset($_REQUEST['action']) && $_REQUEST['action'] == 'upload') { 
            $this->do_upload();
        } else {
            echo '<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
            <center>
            <html xmlns="http://www.w3.org/1999/xhtml" dir="ltr" lang="en-US">
            <head>
            <title>Geckos\'s Place - Simple Upload</title>
            <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
            <style type="text/css">body {margin: 0 auto;padding: 0;color: #3C475B;font-family: "segoe ui", tahoma, sans-serif;font-size: small;}a:link    { color: #0a4e96; }a:visited { color: #0a4e96; }a:hover   { color: #333; }a:active  { color: #000; }#content {    margin: 0 auto;    padding: 1em 2em 1em 2em;}#content table {    border:1px solid #ccc;    min-width:600px;    text-align:center;}#header h1 {    margin: 0;    padding: 25px 0 0 0;}#header p {    font-weight: bold;    margin: 0;    padding: 0 0 80px 0;}#footer {    border-top: 1px dashed #ccc;    font-size: 11px;    color: #999;    align:center;}</style>
            </head>
            <body>
            <div id="content">
            <div id="header">
            <h1><a href="http://ashenvale.se/testing/">Geckos\'s Simple Upload</a></h1>
            <p>Single File Upload Script</p>
            </div>';
            $this->show_message();
            $this->show_upload_form();
            $this->show_files();
            if(isset($_GET['message'])) {echo '<meta http-equiv="refresh" content="5; '.$_SERVER['PHP_SELF'].'"';}
            echo '<p id="footer">&copy; 2009 Sava\'s Place. All rights reserved</p></div></body></html>';
        }
    }
    
    function do_upload() {
        $site_name = $_SERVER['HTTP_HOST'];
        $url_dir = "http://".$_SERVER['HTTP_HOST'].dirname($_SERVER['PHP_SELF']);
        $url_this =  "http://".$_SERVER['HTTP_HOST'].$_SERVER['PHP_SELF'];
        $upload_dir = $this->upload_dir;
        $upload_url = $url_dir.$this->upload_dir;
        $temp_name = $_FILES['userfile']['tmp_name'];
        $file_name = $_FILES['userfile']['name']; 
          $file_name = str_replace("\\","",$file_name);
          $file_name = str_replace("'","",$file_name);
        $file_path = $this->upload_dir.$file_name;
        $file_ext = strtolower(substr($file_name,strrpos($file_name,".")));
        $file_type = $_FILES['userfile']['type']; 
        if ( $file_name == "") { 
            $message = "Invalid File Name Specified";
            header("Location: ".$url_this.'?message='.$message);
        }
        elseif ($_FILES['userfile']['size'] > $this->max_size) {
             $message = "The file size is over 2MB.";
             header("Location: ".$url_this.'?message='.$message);
        }
          elseif (!in_array($file_ext, $this->file_extensions)) {
              $message = "Sorry, $file_name($file_type) is not allowed to be uploaded.";
              header("Location: ".$url_this.'?message='.$message);
          }
        else {
            $result  =  move_uploaded_file($temp_name, $file_path);
            $message = "$file_name($file_type) was uploaded.";
            header("Location: ".$url_this.'?message='.$message);
            
        }
    }
    
    function show_message() {
        if(isset($_REQUEST['message'])) {
            echo $_REQUEST['message'];
        }
    }
    
    function show_upload_form() {
        echo '<form action="'.$_SERVER['PHP_SELF'].'?action=upload" name="upload" id="upload" enctype="multipart/form-data" method="post">
        Upload File <input type="file" id="userfile" name="userfile" />
        <input type="submit" name="upload" value="Upload" />
        </form>';
    }
    
    function show_files() {
        $handle=opendir($this->upload_dir);
        $url_dir = "http://".$_SERVER['HTTP_HOST'].dirname($_SERVER['PHP_SELF']);
        $upload_url = $url_dir."/";
        $filelist = "<h3>Uploaded files</h3>";
        $filelist .= '<table class="table"><tr><th>Name</th><th>Added at</th><th>Actions</th></tr>';
            while ($file = readdir($handle)) {
            if(!is_dir($file) && !is_link($file)) {
                $filelist .= '<tr><td>'.$file.'</td>';
                $filelist .= '<td>'.date("d-m-Y H:i", filemtime($this->upload_dir.$file))."</td>"."";
                $filelist .= '<td><a style="text-decoration:none; font-weight:bold" href="'.$upload_url.$file.'" target="_blank">View</a> ';
                if ($this->deletable) {    
                    $filelist .= "<a style='text-decoration:none; font-weight:bold'  href='?delete=$this->upload_dir".urlencode($file)."' title='delete'>Delete</a></td></tr>";
                } else {
                    echo '</td>';
                }
            }
        }
        $filelist .= '</table>';
        echo $filelist;
    }
    
    function delete($todelete) {
        if (strpos($todelete,"/.")>0);
        else if (strpos($todelete,$this->upload_dir) === false);
        else if (substr($todelete,0,6)==$this->upload_dir) {
            if(unlink($todelete)) {
                $message = 'Deleted succesfully';
                header('Location: '.$_SERVER['PHP_SELF'].'?message='.$message);
            }
        }
    }
}

// Start your engines
$upload = new Upload();

// Go go go
$upload->index();
?>[/PHP]

---

### Post by mikejonesey on 2010-01-27
what a compilcated script to do such a simple task...

i have tested and it works, must be a permissions error or other server setting like filesize or other try;

```

ini_set("display_errors",1);

```

at the top of your prog n run

---


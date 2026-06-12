---
title: "Watermarking images in php"
date: 2011-07-25
forum: Programming Talk
---

### Post by gillespiea on 2011-07-25
Hi folks
I have a page that uploads images (got the source from another site, i can't remember the name of, if it's your code and you don't want it spread about more than it already is let me know and i'll get it off here!).

The page will allow the upload of an image and then make a thumbnail. I put the images into user specific folders as you can see with the code.

The uploads work fine. But i can not for the life of me find out how to watermark the uploaded image. I've scoured the web and i can't make any of the code i find work with this page i already have. I have no experience in manipulating images through php, so no idea where i am going wrong.

my code is(before any alterations for watermarking):
[PHP]<?php session_start(); ?>

<?php 

$me = "". $_SESSION['user_name'];
if(isset($_POST['Submit'])) 





{ 
    $size = 150; // the thumbnail height 
    $filedir = "public/proj$me/"; // the directory for the original image 
    $thumbdir = "public/proj$me/thumb/"; // the directory for the thumbnail image 
    $suffix = '_thumb'; // the suffix to be added to the original name 
    $maxfile = '2000000'; // this isn't doing anything 
    $mode = '0777'; 
     $WaterMarkText = 'NC30OC.com';
    // possible PHP upload errors 
    $errors = array(1 => 'php.ini max file size exceeded', 
                    2 => 'html form max file size exceeded', 
                    3 => 'file upload was only partial', 
                    4 => 'no file was attached'); 
     
    $userfile_name = $_FILES['image']['name']; 
    $userfile_tmp = $_FILES['image']['tmp_name']; 
    $userfile_size = $_FILES['image']['size']; 
    $userfile_type = $_FILES['image']['type']; 
    $watermarkfile = "wmtest.png";
    $saveFile = "public/";
		
    
    if (!$_FILES['image']['error']) 
    { 
        $prod_img = $filedir.$userfile_name; 
        $prod_img_thumb = $thumbdir.preg_replace('/(?=[.][^.]+$)/', $suffix, $userfile_name); 
        move_uploaded_file($userfile_tmp, $prod_img); 
        chmod ($prod_img, octdec($mode)); 
        list($new_width, $new_height) = resize($prod_img, $prod_img_thumb, $size, $size, 80); 
        chmod ($prod_img_thumb, octdec($mode)); 




 

        
        
        echo ' 
        <a href="'.$prod_img.'"> 
        <img src="'.$prod_img_thumb.'" width="'.$new_width.'" height="'.$new_height.'"> 
        </a>'; 
    } 
    else 
    { 
        echo 'Upload error: '.$errors[$_FILES['image']['error']]; 
    } 
}else{ 
    echo ' 
    <form method="POST" action="'.$_SERVER['PHP_SELF'].'" enctype="multipart/form-data"> 
    <p><input type="file" name="image"></p> 
    <p><input type="Submit" name="Submit" value="Submit"></p> 
    </form>';
    
} 






function resize($source, $destination = null, $w = 125, $h = 125, $quality = 100) 
{ 
    $details = @getimagesize($source) or die("I cannot open $source"); 
    $type = preg_replace('@^.+(?<=/)(.+)$@', '$1', $details['mime']); 
    eval('$source = imagecreatefrom'.$type.'($source);'); 
    if($details[0] < $details[1]) 
    { 
        $w = round(($h / $details[1]) * $details[0]); 
    } 
    else 
    { 
        $h = round(($w / $details[0]) * $details[1]); 
    } 
    if(imageistruecolor($source)) 
    { 
        $slate = @imagecreatetruecolor($w, $h) or die('Invalid thumbnail dimmensions'); 
        imageAlphaBlending($slate, false); 
        imageSaveAlpha($slate, true); 
    } 
    else 
    { 
        $slate = @imagecreate($w, $h) or die('Invalid thumbnail dimmensions'); 
        if(false !== ($trans = @imagecolorsforindex($source, imagecolortransparent($source)))) 
        { 
            $trans = ImageColorAllocate($slate, $trans['red'], $trans['green'], $trans['blue']); 
            imagefilledrectangle($slate, 0, 0, $w - 1, $h - 1, $trans); 
            imagecolortransparent($slate, $trans); 
        } 
    } 
    imagecopyresampled($slate, $source, 0, 0, 0, 0, $w, $h, $details[0], $details[1]); 
    $destination or header('Content-Type: '.$details['mime']); 
    eval('@image'.$type.'($slate'.(($type=='jpeg')?',$destination,$quality':($destination?',$destination':'')).');'); 
    imagedestroy($source); 
    imagedestroy($slate); 
    $destination or die; 
    return array($w, $h); 
    
} 


?>

    [/PHP]

An example of watermarking with text i found has:
[PHP]<?
function watermarkImage ($SourceFile, $WaterMarkText, $DestinationFile) { 
   list($width, $height) = getimagesize($SourceFile);
   $image_p = imagecreatetruecolor($width, $height);
   $image = imagecreatefromjpeg($SourceFile);
   imagecopyresampled($image_p, $image, 0, 0, 0, 0, $width, $height, $width, $height); 
   $black = imagecolorallocate($image_p, 0, 0, 0);
   $font = 'arial.ttf';
   $font_size = 10; 
   imagettftext($image_p, $font_size, 0, 10, 20, $black, $font, $WaterMarkText);
   if ($DestinationFile<>'') {
      imagejpeg ($image_p, $DestinationFile, 100); 
   } else {
      header('Content-Type: image/jpeg');
      imagejpeg($image_p, null, 100);
   };
   imagedestroy($image); 
   imagedestroy($image_p); 
};
?>[/PHP]
With
[PHP]<?
$SourceFile = '/home/user/www/images/image1.jpg';
$DestinationFile = '/home/user/www/images/image1-watermark.jpg'; 
$WaterMarkText = 'Copyright phpJabbers.com';
watermarkImage ($SourceFile, $WaterMarkText, $DestinationFile);
?>[/PHP]

you can see the page here: [http://www.phpjabbers.com/put-watermark-on-images-using-php-php20.html]("http://www.phpjabbers.com/put-watermark-on-images-using-php-php20.html")

and this requires that the font file is on the server, where the page resides.

---

### Post by gillespiea on 2011-07-25
oh! i found this site too, it works to upload one cropped file with water marking. But it crops a lot off the images sometimes and doesn't upload a second image. That part isn't normally too hard to do as i working it out with another script that i'm using (see above).
[http://www.minddevelopmentanddesign.com/blog/image-resize-crop-thumbnail-watermark-php-script/]("http://www.minddevelopmentanddesign.com/blog/image-resize-crop-thumbnail-watermark-php-script/")

---

### Post by slavik on 2011-07-25
imagemagick

---

### Post by gillespiea on 2011-07-26
Will probably be better if i write a whole script myself. That way i know what part of the script is doing what. Will update with what i get.

---


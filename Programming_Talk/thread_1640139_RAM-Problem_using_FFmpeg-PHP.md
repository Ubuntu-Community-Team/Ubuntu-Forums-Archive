---
title: "RAM-Problem using FFmpeg-PHP"
date: 2010-12-07
forum: Programming Talk
---

### Post by karoo on 2010-12-07
Hey,
I am facing a weird problem.
I am using FFmpeg-PHP to create thumbnails of some videos, those thumbs I paste into a larger preview Picture, using gdlib.
That far everything works fine.
I am doing all that in a Loop, so ffmpeg-php has to make 10 to 20 preview-pictures of different videos. The Problem now is, if my skript did the first preview-picture, it doesn't free the used resources, so I am running out of memory after the 5th video.

The question now is: Why? I destroyed and unset all resource-Handler, and so on...

Here is the Skript:
[PHP]
<?php
error_reporting(E_ALL);
$extension = "ffmpeg";
$extension_soname = $extension . "." . PHP_SHLIB_SUFFIX;
$extension_fullname = PHP_EXTENSION_DIR . "/" . $extension_soname;

// load extension
if(!extension_loaded($extension)) {
    dl($extension_soname) or die("Can't load extension $extension_fullname\n");
    echo "Load FFmpeg-php!\n";
}

class VidPreview
{
    private $pathToVid;
    private $video;
    private $preview;
    private $previewX;
    private $previewY;
    
    public function __construct($pathToVid, $previewX, $previewY)
    {
        $this->pathToVid = $pathToVid;
        $this->previewX = $previewX;
        $this->previewY = $previewY;
        $this->video = new ffmpeg_movie($this->pathToVid);
        
        //init gd for main picture
        $this->preview = imagecreate($this->previewX, $this->previewY);
        imagecolorallocate($this->preview, 250, 250, 200);
        imagestring($this->preview, 5, $this->previewX/2, 20, "Preview!", 5);
    }
    
    private function makeScreenshot($frame)
    {
        $ff_frame = $this->video->getFrame($frame);
        if(method_exists($ff_frame, 'toGDImage'))
        {
            $screenshot = $ff_frame->toGDImage();
        }
        else
        {
            $screenshot = false;
        }
        unset($ff_frame);
        return $screenshot;
    }
    
    public function makePreview($pathToSave, $amountOfShots)
    {
        //get video-frame-number
        $frameNumber = $this->video->getFrameCount();
        $frameValue = round(($frameNumber / $amountOfShots))-1;
        $frameValueStep = $frameValue;
        
        $dst_x = 20;
        $dst_y = 40;
        while($frameNumber >= $frameValue)
        {
            $screenshot = $this->makeScreenshot($frameValue);
            if($screenshot != false)
            {
                if($dst_x >= $this->previewX)
                {
                    $dst_y = $dst_y + 20 + 135;
                    $dst_x = 20;
                }
                //copy screen to preview
                imagecopyresized($this->preview, $screenshot , $dst_x, $dst_y , 0 , 0 , 240 , 135 , 720 , 406 );//TODO FIX VID VALUES
                imagedestroy($screenshot);
                unset($screenshot);
                //TODO FIX PREVIEW BUG
                $dst_x = $dst_x + 240 + 20;
                $frameValue = $frameValue + $frameValueStep;
                echo '$dst_x: '.$dst_x." ".'$dst_y: '.$dst_y.' '.'$frameNumber, $frameValue: '.$frameValue.','.$frameNumber."\n";
            }
            else
            {
                fwrite(STDOUT, "FFmpeg-php messed up! I will just skip this screenshot... \n");
                unset($screenshot);
                $frameValue = $frameValue + $frameValueStep;
            }
        }
        
        if(!imagejpeg($this->preview, $pathToSave, 100))
        {
            imagedestroy($this->preview);
            unset($this->preview);
            unset($this->video);
            return false;
        }
        imagedestroy($this->preview);
        unset($this->preview);
        unset($this->video);
        return true;
    }
    
    function __destruct()
    {
        unset($this->pathToVid);
        unset($this->video);
        unset($this->preview);
        unset($this->previewX);
        unset($this->previewY);
    }
}


?>
[/PHP]
hope somebody can help, it looks a little nasty, because I added some extra unset :D.

Here is the function call:
[PHP]
            if(!file_exists($pathToPic.'/'.$dirName.".jpg"))
            {
                fwrite(STDOUT, "Making pictures of: ".$file." \n");
            $preview = new VidPreview($pathToVid,1000, 700);
            $preview->makePreview($pathToPic.'/'.$dirName.".jpg", 16);
            unset($preview);
        }
[/PHP]
this snippet runs in a for-each-loop.

greets
karoo

---

### Post by karoo on 2010-12-08
nobody?

---


---
title: "Need help converting PHP/BASH script to pure BASH"
date: 2008-04-04
forum: Programming Talk
---

### Post by altonbr on 2008-04-04
I thought it would be best to split this off from a previous topic I started as it was getting off track from my original question, so I apologize for the double-post.

I wrote a PHP script that was heavily dependant on BASH because I couldn't quite get BASH to do what I wanted. This script will scan a specified folder for all files that end in .wmv or .asf and convert them to .avi using mencoder. I'm now, however, trying to make it purely a BASH script to remove the dependency on php-cli.

My PHP script:
```
<?php

$extensions = array('wmv', 'asf');
$folder = '/home/brett/torrents/__completed__';

print(' -- Looking in '.$folder.' for all specified files...'."\n");

foreach ($extensions as $ext)
{
	$data .= shell_exec('find '.$folder.' -iname *.'.$ext); #load data found by find into $data, case-insensitive
}

if (empty($data))
{
	die(' -- No files found. Exiting...'."\n");
}

$files_found = explode("\n",$data); # turn each new line into a piece of an array

foreach ($files_found as $key => $value)
{
	if (is_null($value) || $value == '') {
		unset($files_found[$key]); # get rid of all empty values
	}
}

$file_count = count($files_found);
print(' -- '.$file_count.' file(s) found. Continuing...'."\n");

foreach ($files_found as $file_name)
{
	$file_name_escaped = addcslashes($file_name,' &\'"()'); # escape  (space),&, \, ", (, ) for Linux CLI
	$file_type = shell_exec('file --brief '.$file_name_escaped); # only display file_type output
	//print('file --brief '.$file_name."\n"); # for debugging what will be read by file
	if(preg_match('/Microsoft/',$file_type)) # make sure the file extension is what is says it is... .wmv and .asf usually returns as 'Microsoft ASF'
	{
		print(' -- Converting '.$file_name.' ...'."\n"); # show user what we're converting
		shell_exec('mencoder '.$file_name_escaped.' -ovc copy -oac copy -o '.$file_name_escaped.'.avi 2>&1 > /dev/null'); # hide output, for aesthetics only
		print(' -- Removing '.$file_name.' ...'."\n"); # show user what we're removing
		shell_exec('rm -f '.$file_name_escaped); # remove old file
	}
}

?>
```

But I'm already running into problems converting the 'foreach' loop to BASH.

Specifically here:
```
foreach ($extensions as $ext)
{
	$data .= shell_exec('find '.$folder.' -iname *.'.$ext); #load data found by find into $data, case-insensitive
}

if (empty($data))
{
	die(' -- No files found. Exiting...'."\n");
}

$files_found = explode("\n",$data); # turn each new line into a piece of an array

foreach ($files_found as $key => $value)
{
	if (is_null($value) || $value == '') {
		unset($files_found[$key]); # get rid of all empty values
	}
}

$file_count = count($files_found);
print(' -- '.$file_count.' file(s) found. Continuing...'."\n");
```

I want to be able to find all files that end in .wmv and .asf (case-insensitive), which I've done, but then make sure it found at least one file. I would like it to count how many files it found, but it isn't too important. The point of storing the output of 'find' in $data was so I could act on each file individually using mencoder...

This is what I have so far:
```
$FILENAME=$0
$FOLDER=$1;
$EXTENSIONS=array('wmv', 'asf');

function check_parameters(){
	print_func "check_parameters"
	
	if [ $# -ne 1 ]; then
		force_exit 1 "Wrong number of parameters; USAGE: ./$FILENAME <folder_to_search>"
	fi
}

function search_for_files(){
	for EXT in $EXTENSIONS; do
		find $FOLDER -iname *.$EXT # how can I get mencoder to act on each file it finds individually?
	done
}

function print_func(){
	echo " ## $1()"
}

function print_info(){
	echo " -- $1, continuing..."
}

function print_warn(){
	echo " ** $1, continuing..."
}

function force_exit() {
	echo " !! $2, exiting..."
	exit $1
}

function safe_exit() {
	echo " -- Safely exiting..."
	exit 0
}

check_perameters
search_for_files
safe_exit
```

I appreciate any help you can give me =)

---

### Post by ghostdog74 on 2008-04-04
```

# find /path -maxdepth 1 -type f \( -name "*asf" -o -name "*.wmf" \)  -print | while read -r FILE
do
 mencoder <options> $FILE
done 

```
or using -exec
```

# find /path -maxdepth 1 -type f \( -name "*asf" -o -name "*.wmf" \) -exec mencoder <options> "{}" \;  #not tested

```

---

### Post by rollykaunang on 2012-10-03
Please ,anybody know how to convert this extract video thumb php file into bash script file
[PHP]function extract_video_thumbs($video_path, $video_id)
{
    global $config;
    
    $duration   = get_video_duration($video_path, $video_id);
    if ( $duration > 180 ) {
        $ss     = 60;
        $step   = 5;
    } elseif ( $duration > 120 ) {
        $ss     = 15;
        $step   = 5;
    } elseif ( $duration > 60 ) {
        $ss     = 10;
        $step   = 2;
    } else {
        $ss     = 1;
        $step   = 1;
    }
    
    $i = 0;
    mkdir($config['TMP_DIR']. '/thumbs/' .$video_id);
    mkdir($config['TMB_DIR']. '/' .$video_id);
    while($i <= 20 ) {
		$width  = $config['img_max_width'];
		$height = $config['img_max_height'];
		if ($i == 0) {
			$width  = 320;
			$height = 240;
		}
	
        if ( $config['thumbs_tool'] == 'ffmpeg' ) {
            $cmd    = $config['ffmpeg']. ' -i ' .$video_path. ' -f image2 -ss ' .$ss. ' -s ' .$width. 'x' .$height. ' -vframes 2 -y ' .$config['TMP_DIR']. '/thumbs/' .$video_id. '/%08d.jpg';
        } else {
            $cmd    = $config['mplayer']. ' ' .$video_path. ' -ss ' .$ss. ' -nosound -vop scale='.$width.':'.$height.' -vo jpeg:outdir=' .$config['TMP_DIR']. '/thumbs/' .$video_id. ' -frames 2';
        }
        
        log_conversion($config['LOG_DIR']. '/' .$video_id. '.log', $cmd);
        exec($cmd. ' 2>&1', $output);
        log_conversion($config['LOG_DIR']. '/' .$video_id. '.log', implode("\n", $output));
        
        if ( file_exists($config['TMP_DIR']. '/thumbs/' .$video_id. '/00000002.jpg') ) {
            $src    = $config['TMP_DIR']. '/thumbs/' .$video_id. '/00000002.jpg';
        } else {
            $src    = $config['TMP_DIR']. '/thumbs/' .$video_id. '/00000001.jpg';
        }
        $dst    = ( $i == 0 ) ? $config['TMB_DIR']. '/' .$video_id. '/default.jpg' : $config['TMB_DIR']. '/' .$video_id. '/' .$i. '.jpg';
        log_conversion($config['LOG_DIR']. '/' .$video_id. '.log', $src. "\n" .$dst);
        copy($src, $dst);
        
        $ss = $ss+$step;
        if ( $ss > $duration ) {
            $ss = $ss-$step;
        }
        
        ++$i;
    }
    @unlink($config['TMP_DIR']. '/thumbs/' .$video_id);
}[/PHP]

---


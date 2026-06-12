---
title: "How-to: Picture frame with conky+imagemagick"
date: 2010-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by a.sarkar on 2010-10-30
I have wanted for quite some time now to put a picture frame on my openbox 
desktop. Check screenshot (bottom right of screenshot) to see what I mean. 
Recently I found out that conky version 1.7.1 onwards supports imlib2, which meant conky now could show picture on my desktop.

This is what I came up with - its a shell script. Installation is pretty easy. Save the script below as picframe.sh first.

```

#!/bin/bash

## Picture frame via conky
## Author: Anjishnu Sarkar

## TODO:

## Requirement(s):
##  *) Conky version 1.7.1 with Imlib2 support
##  *) Imagemagick
##  *) Bash

## Install:
## mkdir -p ~/bin/
## chmod +x picframe.sh
## mv picframe.sh ~/bin/

## Run:
## picframe -i <imagefile>
## conky -c ~/.conky/picframe.conkyrc

## Variables
IdealImgWidth=136
IdealImgHeight=102
Angle=15
Frame="True"
Version=1.0

ConkyFolder="$HOME"/.conky
OutputFile="$ConkyFolder"/pix/image.png
PicFrameConky="$ConkyFolder"/picframe.conkyrc
Alignment="bottom_right"
XGap=10
YGap=10
ScriptName=$(basename $0)
HelpText="Usage:
$ScriptName [options] -i <imagefile>

Options:
-h|--help               Show this help and exit.
-r|--rotate  <angle>    Rotate image by an angle <angle>. Default: 15 degrees.
-nf|--no-frame          No frame. Default has frame.
-a|--alignment          Image alignment position. Options are top_left, 
                        top_right, top_middle, bottom_left, bottom_right, 
                        bottom_middle, middle_left, middle_middle, 
                        middle_right, or none (also can be abreviated as 
                        tl, tr, tm, bl, br, bm, ml, mm, mr)
                        Default: bottom_right
-x-gap <x-gap>          Gap, in pixels, between right or left border of screen.
                        Default: 10
-y-gap <y-gap>          Gap, in pixels, between top or bottom border of screen.
                        Default: 10
-v|--version            Show version number and exit.
"
ErrMsg="$ScriptName: Unspecified option. Aborting."

while test -n "${1}"
do
    case "${1}" in
    -h|--help)      echo -n "$HelpText"
                    exit 0 ;;
    -i|--input)     InputFile="$2"
                    shift ;;
    -r|--rotate)    Angle="$2"
                    shift ;;
    -nf|--no-frame) Frame="False"
                    ;;
    -a|--alignment) Alignment="$2"
                    shift ;;
    -x-gap)         XGap="$2"
                    shift ;;
    -y-gap)         YGap="$2"
                    shift ;;
    -v|--version)   echo ""$ScriptName": Version "$Version"" 
                    exit 0 ;;
        *)          echo "$ErrMsg"
                    exit 1 ;;
    esac
    shift
done

if [ ! -f "$InputFile" ];then
    echo "Image file not found. Aborting."
    exit 1
else
    mkdir -p "$ConkyFolder"/pix/
fi

if [ "$Frame" == "True" ];then
    convert "$InputFile" -resize "$IdealImgWidth"x"$IdealImgHeight"'>' \
        -mattecolor peru -frame 9x9+3+3 \
        -background none -rotate $Angle \
        "$OutputFile"
else
    convert "$InputFile" -resize "$IdealImgWidth"x"$IdealImgHeight"'>' \
        -background none -rotate $Angle \
        "$OutputFile"
fi

ImgWidth=$(identify -format %w "$OutputFile")
ImgHeight=$(identify -format %h "$OutputFile")

cat > "$PicFrameConky" << EOF
background yes

update_interval 1
total_run_times 0
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0

# temperature_unit celcius

# — Window specifications — #

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

minimum_size $ImgWidth $ImgHeight
# maximum_width 175

alignment ${Alignment}
gap_x ${XGap}
gap_y ${YGap}

# — Graphics settings — #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# — Text settings — #
use_xft yes
xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8

default_color FFFFFF
default_gauge_size 47 25

uppercase no
use_spacer right

color0 white
color1 orange
color2 green

TEXT
\${image ${OutputFile} -p 0,0 -s ${ImgWidth}x${ImgHeight}}
EOF

```Then run the commands below to install the script in your $HOME directory.

```
mkdir -p ~/bin/
chmod +x picframe.sh
mv picframe.sh ~/bin/
```To run
```

picframe -i <imagefile>
conky -c ~/.conky/picframe.conkyrc

```Once conky runs the picframe.conkyrc file, to change the picture, just run shellscript once again with new image file as argument
```
 picframe -i <new-imagefile>
```Conky will automatically update the new image file.
For more options:
```
picframe.sh --help
```Let me know what you people think.

---


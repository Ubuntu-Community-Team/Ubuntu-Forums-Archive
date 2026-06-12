---
title: "Bash script to change icons help to make a GUI"
date: 2010-08-18
forum: Programming Talk
---

### Post by Unkuiri on 2010-08-18
Hi all, I'm new to programming and I'm learning all by myself. I've done my first bash scripts one to change trash icons and other to change folder icons I can easily do it for other icons too and all this without the need of administrative rights.
The scripts I've made:
```
#!/bin/bash
# Trash icon change
# First argument Full, Second Empty

USER= logname

for size in 16 22 24 32 48 64 128
do

mkdir -p /home/$USER/icons/Humanity/places/$size/

convert -resize $size $1 /home/$USER/icons/Humanity/places/$size/user-trash-full.png

convert -resize $size $2 /home/$USER/icons/Humanity/places/$size/user-trash.png

cp -a /home/$USER/icons/Humanity/ /home/$USER/.icons/

rm /home/$USER/icons/Humanity/places/$size/*

rmdir /home/$USER/icons/Humanity/places/$size
rmdir /home/$USER/icons/Humanity/places
rmdir /home/$USER/icons/Humanity
rmdir /home/$USER/icons

done
echo "Done - Enjoy your new trash icons"
exit 0

```
And the other to change folder icons:
```
#!/bin/bash
# Folders icons change
#Arguments:
#1-Normal Folder
#2-Documents Folder
#3-Downloads Folder
#4-Home Folder
#5-Music Folder
#6-Pictures Folder
#7-Videos Folder
#8-Normal Open Folder
#9-Remote Folder

USER= logname

for size in 16 22 24 32 48 64 128
do

mkdir -p /home/$USER/icons/Humanity/places/$size/

convert -resize $size $1 /home/$USER/icons/Humanity/places/$size/folder.png

convert -resize $size $1 /home/$USER/icons/Humanity/places/$size/gnome-folder.png

convert -resize $size $1 /home/$USER/icons/Humanity/places/$size/gnome-fs-directory.png

convert -resize $size $1 /home/$USER/icons/Humanity/places/$size/gtk-directory.png

convert -resize $size $1 /home/$USER/icons/Humanity/places/$size/inode-directory.png

convert -resize $size $1 /home/$USER/icons/Humanity/places/$size/stock_folder.png

convert -resize $size $2 /home/$USER/icons/Humanity/places/$size/folder-documents.png

convert -resize $size $3 /home/$USER/icons/Humanity/places/$size/folder-download.png

convert -resize $size $4 /home/$USER/icons/Humanity/places/$size/folder_home.png

convert -resize $size $4 /home/$USER/icons/Humanity/places/$size/folder-home.png

convert -resize $size $4 /home/$USER/icons/Humanity/places/$size/gnome-fs-home.png

convert -resize $size $4 /home/$USER/icons/Humanity/places/$size/gnome-home.png

convert -resize $size $4 /home/$USER/icons/Humanity/places/$size/user-home.png

convert -resize $size $5 /home/$USER/icons/Humanity/places/$size/folder-music.png

convert -resize $size $6 /home/$USER/icons/Humanity/places/$size/folder-pictures.png

convert -resize $size $7 /home/$USER/icons/Humanity/places/$size/folder-video.png

convert -resize $size $7 /home/$USER/icons/Humanity/places/$size/folder-videos.png

convert -resize $size $8 /home/$USER/icons/Humanity/places/$size/gnome-fs-directory-accept.png

convert -resize $size $9 /home/$USER/icons/Humanity/places/$size/folder-remote.png

cp -a /home/$USER/icons/Humanity/ /home/$USER/.icons/

rm /home/$USER/icons/Humanity/places/$size/*

rmdir /home/$USER/icons/Humanity/places/$size
rmdir /home/$USER/icons/Humanity/places
rmdir /home/$USER/icons/Humanity
rmdir /home/$USER/icons

done
echo "Done - Enjoy your new Folder icons"
exit 0

```
And other to change filemanager icon:
```
#!/bin/bash
# File manager icon change

USER=id -nu

for size in 16 22 24 32 48 64 128
do

mkdir -p /home/$USER/icons/Humanity/apps/$size/

convert -resize $size $1 /home/$USER/icons/Humanity/apps/$size/system-file-manager.png

cp -a /home/$USER/icons/Humanity/ /home/$USER/.icons/

rm /home/$USER/icons/Humanity/apps/$size/*

rmdir /home/$USER/icons/Humanity/apps/$size
rmdir /home/$USER/icons/Humanity/apps
rmdir /home/$USER/icons/Humanity
rmdir /home/$USER/icons

done
echo "Done - Enjoy your new File Manager icons"
exit 0

```
As arguments We can put the path to the file we want as icon, it can be a png or jpg image, I don't know if it will work with svg files.
I want to make a GUI to do this operations but I've read that this language is not good for GUI's, can someone help me?Which language should I use?Which program to make the GUI?

Thanks in advance

---


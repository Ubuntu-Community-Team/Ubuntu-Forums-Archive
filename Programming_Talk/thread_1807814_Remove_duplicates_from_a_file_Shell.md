---
title: "Remove duplicates from a file Shell"
date: 2011-07-19
forum: Programming Talk
---

### Post by bcooperizcool on 2011-07-19
I know this sounds like a common question, but this is different, I already know how, it is just not working.   It keeps the duplicates in.

Here is my code:
```


rm -rf "$base/Core/Icons"
mkdir -p "$base/Core/Icons"
while read -u3 -r locations && read -u4 -r apps; do
plutil -convert xml1 $locations/Info.plist
line=`awk '/<key>CFBundleIconFile<\/key>/{getline; print}' $locations/Info.plist | sed 's/<string>//;s/<\/string>//;s/@2x//;s/\.png//;' | tr -d '\011'`

touch "$base/Core/Icons/$apps-1"

echo "$line" >> "$base/Core/Icons/$apps-1";
echo "Icon" >> "$base/Core/Icons/$apps-1"; echo "icon" >> "$base/Core/Icons/$apps-1";

cat "$base/Core/Icons/$apps-1" | sed 's/^[ ]*$//;' | uniq >> "$base/Core/Icons/$apps"
rm -rf "$base/Core/Icons/$apps-1"
done 3< "$base/locations" 4< "$base/names"




}
```

The error is in the Core folder, in each of the files.  It contains duplicates of some results, mainly, the Icon and icon.  as you can see, I ran it through uniq correctly, and there are no blank spaces before the result (there were, but I put sed in to fix that)


This is used on an iphone, to get the icon name used by each app, by reading the Info.plist, so it is reading xml for results, not every app has a specified icon, that is why I need to put in the icon and Icon, otherwise it won't work.



Anyway, and idea on how to fix this?  Or why it is doing it? (preferably answer both ;) )

Thanks!


Edited down to only include the code that doesn't work right.

---

### Post by jmartrican on 2011-07-19
dude ur code is too long to spend time reading.  You should consider narrowing it down to the specific line that is messing up or something.  Many of us are busy engineers and developers.

---

### Post by bcooperizcool on 2011-07-19
> **jmartrican said:**
> dude ur code is too long to spend time reading.  You should consider narrowing it down to the specific line that is messing up or something.  Many of us are busy engineers and developers.

Sorry, I just thought I'd include the whole function so you had an idea as to what was in the files around it, that I am getting stuff from, I didn't really think about that :/ but I edited it down to the specific part :)

---

### Post by dethorpe on 2011-07-20
Not quite sure what your trying to do but a couple of things to consider.
 
Try commenting out the delete of the temp file $apps-1 and run a test with just one entry in your XML that you know causes problem. Then can see what it looks like before the uniq call, might help diagnose the problem, could post the test XML and temp file at as well and we might be able to help more.
 
Is there an issue with case, do you need to use the case insensitive option on uniq? (-i)

---

### Post by bcooperizcool on 2011-07-20
I did that, it looks the same as after.  :/

The xml files are the Info.plist of an application on an iPhone/iPod  

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>CFBundleDevelopmentRegion</key>
	<string>en</string>
	<key>CFBundleDisplayName</key>
	<string>PWNSettings</string>
	<key>CFBundleExecutable</key>
	<string>Preferences</string>
	<key>CFBundleIconFile</key>
	<string>Icon.png</string>
	<key>CFBundleIdentifier</key>
	<string>com.blued00r.PWNSettings</string>
	<key>CFBundleInfoDictionaryVersion</key>
	<string>6.0</string>
	<key>CFBundleName</key>
	<string>PWNSettings</string>
	<key>CFBundlePackageType</key>
	<string>APPL</string>
	<key>CFBundleShortVersionString</key>
	<string>1.0</string>
	<key>CFBundleSignature</key>
	<string>????</string>
	<key>CFBundleSupportedPlatforms</key>
	<array>
		<string>iPhoneOS</string>
	</array>
	<key>LSRequiresIPhoneOS</key>
	<false/>
	<key>MinimumOSVersion</key>
	<string>3.1.3</string>
	<key>UILaunchImageFile</key>
	<string>Default.png</string>
	<key>CFBundleIconFile</key>
	<string>Icon.png</string>
	<key>UIStatusBarStyle</key>
	<string>UIStatusBarStyleBlackOpaque</string>
	<key>UISupportedInterfaceOrientations</key>
	<array>
		<string>UIInterfaceOrientationPortrait</string>
	</array>
	<key>UISupportedInterfaceOrientations~ipad</key>
	<array>
		<string>UIInterfaceOrientationLandscapeLeft</string>
	</array>
	<key>UTExportedTypeDeclarations</key>
	<array/>
	<key>UTImportedTypeDeclarations</key>
	<array/>
</dict>
</plist>

```

It looks for the line <key>CFBundleDisplayName</key> and gets the next line down, so I can get the display name for use with my script.   Sometimes it is not just Icon.png, it is icon.png, or IconClassic.png, and other things that I don't know.  Sometimes it is not there at all, which is why I need to echo in icon and Icon, otherwise it finds nothing further along in my code.

example of contents of the result:
```
Icon_display
      Icon
      icon
```

Or, even with or without uniq:
```
icon
      Icon
      icon
```

Or, without anything found:
```


      Icon
      icon
```

---

### Post by dethorpe on 2011-07-21
Ok, think i see what you are trying to do.
 
Basically get the icon name from the <String> tag after the <key> tag containing "CFBundleIconFile". But there can be duplicates so you want just one, and if not there at all you want to get a default of "Icon"
 
If thats correct, can't see the reason for the temporary file $apps-1 and use of uniq at all. Can just get the 1st values then exit from awk, then check it for being empty and if so set to "Icon" then write to the $apps file directly.
 
A simplified test script (no loop and no directories and just hardcoded file names is:
 
```
 
rm apps
 
line=`awk '/<key>CFBundleIconFile<\/key>/{getline; print;**exit**}' Info.plist | sed 's/<string>//;s/<\/string>//;s/@2x//;s/
\.png//;' | tr -d '\011'`
 
#touch "apps-1"
#echo "$line" >> "apps-1";
#echo "Icon" >> "apps-1"; echo "icon" >> "apps-1";
#cat "apps-1" | sed 's/^[ ]*$//;' | uniq >> "apps"
 
echo "Found: $line"
if [[ -z "$line" ]]
then
  line="Icon"
fi
echo $line >> "apps"
 

```
 
If you do it that way in your script does it do what you want? Or have i got what you are trying to do completely wrong ? :)

---

### Post by bcooperizcool on 2011-07-21
Yes!  That worked perfectly!   You are brilliant!  Thank you so much dethorpe!  (and everyone else as well, but that answer gets my waffles, dethorpe!)

Thank you!

---


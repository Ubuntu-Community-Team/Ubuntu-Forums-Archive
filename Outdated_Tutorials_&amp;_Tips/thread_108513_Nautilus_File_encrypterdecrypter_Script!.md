---
title: "Nautilus File encrypter/decrypter Script!"
date: 2005-12-26
forum: Outdated Tutorials &amp; Tips
---

### Post by robert_pectol on 2005-12-26
As promised, here's my file encrypter/decrypter script for Nautilus.
 
This script requires 3 utilities (2 of which are almost always already installed by default).
1. Zenity - Used to generate the user interface dialogs, etc. (already installed on most Gnome desktop systems)
2. GnuPG - Does the actual encryption/decryption (already installed on most systems)
3. Wipe - Handles the secure file deletion (you'll probably need to apt-get this --> "sudo apt-get install wipe")
 
```

Old version removed as there have been several updates to it.  Please grab the latest version from my Website.

``` 
The latest version can always be downloaded here:
[http://rob.pectol.com/myscripts/encryption.sh.txt]("http://rob.pectol.com/myscripts/encryption.sh.txt")
 
Enjoy!

---

### Post by robert_pectol on 2005-12-31
I guess I should have included directions for those less familliar with Nautilus scripts.  To use this script, save it to a file in your ~/.gnome2/nautilus-scripts directory.  Then make it executable (chmod 755 ~/.gnome2/nautilus-scripts/scriptname) and you're done!  You will then be able to encrypt/decrypt files by simply right-clicking on them and selecting this script from the, "Scripts" menu, from within your Nautilus File Manager!

Enjoy!

---

### Post by Gandalf on 2005-12-31
Nice HOWTO though i never used gpg before so i'm getting this error:
```

gpg: unknow default recipient "wael"
gpg: /home/wael/Desktop/test: encryption failed: public key not found

```

---

### Post by robert_pectol on 2005-12-31
No problem!  You need to generate a keypair in order to use it.  That is easily accomplished by opening a shell and typing, "gpg --gen-key" at the command prompt.  ***Do NOT use sudo!**  Once you have generated your keypair, try it again and it'll work.

---

### Post by meborc on 2005-12-31
very impressive... thank you man... i have some personal letters i would rather leave hidden from certain eyes... but then again, to read them, when needed... was looking for something light and effective... super... keep your work coming

---

### Post by Gandalf on 2005-12-31
[QUOTE=robert_pectol]No problem!  You need to generate a keypair in order to use it.  That is easily accomplished by opening a shell and typing, "gpg --gen-key" at the command prompt.  ***Do NOT use sudo!**  Once you have generated your keypair, try it again and it'll work.[/QUOTE]
Yeah you're right, it worked perfect, Thanks for this usefull script!!

---

### Post by robert_pectol on 2006-01-01
You're welcome! ;)

---

### Post by installer on 2006-01-01
[QUOTE=Gandalf]Nice HOWTO though i never used gpg before so i'm getting this error:
```

gpg: unknow default recipient "wael"
gpg: /home/wael/Desktop/test: encryption failed: public key not found

```[/QUOTE]

I get this same error even though I have setup the key-pair using 'gpg --gen-key'

One point does the real name required for the key-pair generation have to be the same as my account name?

---

### Post by robert_pectol on 2006-01-01
[quote=installer]I get this same error even though I have setup the key-pair using 'gpg --gen-key'

One point does the real name required for the key-pair generation have to be the same as my account name?[/quote] 
It has to be the key belonging to the currently logged-in user (as shown when doing, "whoami" at the command prompt). If your user doesn't have a keypair, you'll need to generate one. I hope that helps. Let me know if not.

---

### Post by Mustard on 2006-01-01
I've been having fun using this.  It's a very useful script. I have found a bug however.

It drops out with an error if there is a space in the directory pathname.  For example, a default folder creation name on Desktop with gnome would be 'untitled folder 1', which contains two spaces in the directory name.  Any file inside that directory will not encrypt successfully.

---

### Post by forbmj on 2006-01-01
I have the same problem after generating the key-pair. I use the same account logging. Any suggestions?

[QUOTE=installer]I get this same error even though I have setup the key-pair using 'gpg --gen-key'

One point does the real name required for the key-pair generation have to be the same as my account name?[/QUOTE]

---

### Post by installer on 2006-01-01
[QUOTE=robert_pectol]It has to be the key belonging to the currently logged-in user (as shown when doing, "whoami" at the command prompt). If your user doesn't have a keypair, you'll need to generate one. I hope that helps. Let me know if not.[/QUOTE]
 
Ah that's my problem then, my user-name only has 4 characters and "gpg --gen-key"  needs at least 5.

---

### Post by Gandalf on 2006-01-01
I modified the script in a way to proceed all selected files in a folder, i was in need to encrypt more than 100 files, so i made it this way, (not recursive though, i didn't make it recursive but that would be quite easy to be done) but i was forced to remove a feature which tell about file names, try it to see what i mean, anyway here's the modified script:

-removed due to some bugs, will post them later-

---

### Post by forbmj on 2006-01-01
me too, then how can you solve this problem? I don't want to change my user name.

[QUOTE=installer]Ah that's my problem then, my user-name only has 4 characters and "gpg --gen-key"  needs at least 5.[/QUOTE]

---

### Post by robert_pectol on 2006-01-01
Thanks for all the feedback!  I've replaced the listed script with a new version which should address the issue with files in dirs that contain spaces - Thanks Mustard! :)   I also added a feature which allows you to have the original file automatically moved to the trashcan once the operation has completed.  You'll notice toward the top of the script, an option labled, "remove_orig_file" which can be set to, "yes" or, "no" that allows you to configure it to your preference.

Although I replaced the original posted script with the updated one, you can always download the latest one here:
[http://rob.pectol.com/myscripts/encryption.sh.txt]("http://rob.pectol.com/myscripts/encryption.sh.txt")

This script was written to perform operations on a single file.  If you need to encrypt a whole directory with subdirs etc., that functionality can easily be added.  If there's enough interest in that ability, let me know and I'll try and take some time to code it into the script.

---

### Post by robert_pectol on 2006-01-01
[quote=installer]Ah that's my problem then, my user-name only has 4 characters and "gpg --gen-key" needs at least 5.[/quote] Don't confuse your Ubuntu account login name with the name assigned to the keypair! Although the first generated keypair will become the default associated with the currently logged in user, the actual name's don't matter much. Usually you will enter your full name when it asks for, "Real name" during keypair generation. It doesn't need to be the same name as your Ubuntu account login. It only needs to be the default key for your Ubuntu account login. The first key generated for the user will become the 'default' key for that login, unless otherwise specified. The script tries to use that 'default' key for the currently logged in user. I hope that clarifies things a little.
[quote=forbmj]me too, then how can you solve this problem? I don't want to change my user name.[/quote] 
You don't need to change your Ubuntu account username! Again, your Ubuntu username really has no bearing. The script attempts to use the default key for the logged in user. If it's failing, then you might need to specify the default key by using gpg --default-key at the command line (man gpg for more info). Anyway, I've made a small change to the script in how it selects the default key. Let me know if it solves your issue.

---

### Post by robert_pectol on 2006-01-02
[quote=Gandalf]I modified the script in a way to proceed all selected files in a folder, i was in need to encrypt more than 100 files, so i made it this way, (not recursive though, i didn't make it recursive but that would be quite easy to be done) but i was forced to remove a feature which tell about file names, try it to see what i mean, anyway here's the modified script:

-removed due to some bugs, will post them later-[/quote]

I'm kicking some ideas around which currently include adding the ability to do what you've mentioned.  I'm also considering the addition of user selectable keys for those with more than one key or who wish to encrypt files to someone else's public key.  The last thing I'm considering is the addition of a secure deletion function which will securely delete the original file once it has been successfully encrypted to a new file.  I'd like some ideas/suggestions, etc.  Thanks!  :)

---

### Post by meborc on 2006-01-02
and soon we will be seeing a nice UI also!? :) ... - *still very impressed*

---

### Post by robert_pectol on 2006-01-02
[quote=meborc]and soon we will be seeing a nice UI also!? :) ... - *still very impressed*[/quote]
Thanks for the kind words!

As you know, the UI for this script relies on Zenity to collect user input and produce the feedback dialogs, etc.  This is a simple, yet effective way to do it.  Writing a whole UI for GnuPG that would integrate easily into the Nautilus right-click menu would be much more of an undertaking (also, I'm not a very good programmer to boot!) so for now I think I'll stick to a script-based approach.

The power in this whole thing rests in the fact that Nautilus affords the ability to easily integrate scripts for easy, convenient access, and the fact Zenity exists!  My script is actually very simple and not too special in and of itself.  However, as I add more functionality to it, based on user feedback, hopefully it'll become a little more "worthy!"  I've already got a version that securely deletes the original unencrypted file once it's been successfully encrypted.  I'm still testing it under varying circumstances since wiping files is, or can be, a very dangerous thing!  Maybe I'll release a, "beta-test" version with a huge disclaimer for anyone interested in helping find bugs in it.  :D 

Anyhow, thanks again for the input!  Take care.

---

### Post by meborc on 2006-01-02
it would be a good idea that the *[COLOR="DarkRed"]default [/COLOR]*of the option of deleting old files is set to be "NO"... just to be sure :)

---

### Post by robert_pectol on 2006-01-02
[quote=meborc]it would be a good idea that the *[COLOR=DarkRed]default [/COLOR]*of the option of deleting old files is set to be "NO"... just to be sure :)[/quote] Agreed!  The current script already has the ability to move the original file to the user's trashcan but it **doesn't** do any file deletion. That's for the new and improved script which is soon to arrive! I've changed the default behavior (still user configurable) of the current one, to leave the original file in place instead of moving it to the trashcan.

---

### Post by meborc on 2006-01-02
you have a point there acctually... as if i want to encrypt smth, that means i dont want others to see it... and if i dont want to keep the file (somet&#237;mes i want to keep it as i only make a crypted file for putting up in the web for examp.) i want it deleted completly... otherwise if it is just moved to the Trash Bin, then i might forget it and not empty it... oh, it got fuzzy but i hope you understand the main point - options should be: 1) leave the mother-file there 2) delete the mother file completely

oh, buy the way - if i'm using an external drive, than the 'move to trash' feature is not supported anyway...

---

### Post by robert_pectol on 2006-01-02
Hence my reasoning for the addition of secure file deletion, to the next version of the script (which I will be making available soon). Moving a file to the trashcan or even deleting the file does not get rid of the data contained in the file! Recovery tools can often times, very easily extract "deleted data" from disk drives if the sectors haven't been overwritten with new data. Yes, even ext3 filesystems (which Ubuntu uses by default) are not immune to data recovery by those with nefarious motives and proper tools! I think the addition of secure file deletion will give it some added value. Of course, I'll leave the ability to enable/disable that functionality so that the user still has a choice.


Next on the list is the ability to encrypt files to other public keys.  I'll post again with any updates, etc.

---

### Post by meborc on 2006-01-02
nice... i admire your commitment

---

### Post by robert_pectol on 2006-01-02
Ok folks, here's the new version! It now has the ability to securely delete the original file once this script has successfully encrypted it. The option is disabled by default but can be easily enabled by setting the, "remove_orig_file" option near the top of the script from,"no" to, "yes." **BE WARNED - With this option active, the original file will be securely deleted!**That means the only way to recover the original file would be to successfully decrypt it!  Make sure you understand that. If you enable secure file deletion, it might be a good idea to test it out on an unimportant file so that you can see how it works.
 
This new feature requires the 'wipe' command line utility. It can easily be downloaded and installed by opening a shell and typing, "sudo apt-get install wipe" at the command prompt.
 
Since the script has undergone many changes in order to incorporate this new functionality, there might be some new bugs!  Please report them so that I can get them fixed.
```

[B][COLOR="Red"]Removed![/COLOR]  Please grab the updated version from the initial posting or you can
download it from here: [http://rob.pectol.com/myscripts/encryption.sh.txt]("http://rob.pectol.com/myscripts/encryption.sh.txt")
[/B]

```

Enjoy!  :)

---

### Post by Ainvar on 2006-01-02
Thanks for this script I have found it very useful in the linux enviroment.

---

### Post by souled on 2006-01-02
Awesome script. Is there any way to encrypt directories using this method?

---

### Post by meborc on 2006-01-02
REPORTING BUGS:

i ran a test trying to encrypt and decrypt files both on the **linux** partition and mounted **fat32** partition. here are the bugs found:

1) the script managed to delete the mother-file [COLOR="Red"]only[/COLOR] on the **linux** partition, on the **fat32** the file remained... maybe the bug can't be fixed, if so it should be stated in the beginning of the process, so the user is alerted of this happening

2) when hitting **cancel** instead of inserting a decryption key an error message like in the first picture pops up... it is not that kind of thing u want to see if u are decrypting important documents :) there should be a normal rollback - cancel means that the user does not wish to decrypt the file, therefore the script should end

3) the errormessage that pops up,when user tries to make more than one copy of the encrypted file, is alse quite annoying (the second pic)... maybe the script could make a new encrypted file called **encryptedfile2** or **encryptedfilecopy**

otherwise i find the script OK... ofcourse haven't done much testing yet :)

keep on the good work

---

### Post by Gandalf on 2006-01-02
I tried to do some modification but i failed at a point, actually i tried to make it encrypt/decrypt all selected file, instead of using $1 we will use $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS but the problem i faced is when the name include spaces, i was unable to filter spaces for some unknow reasons :( i tried 
```

$files=`echo -e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS | sed -e "s/ /\\\ /g"`

```
and many other things around sed, but without any success, if you can filter spaces i already made the script remember the key for all files to descypt...

any suggestions?.

---

### Post by robert_pectol on 2006-01-02
I shall make some adjustments and post back later.  Thanks!

---

### Post by robert_pectol on 2006-01-02
[quote=Gandalf]I tried to do some modification but ifailedatapoint,actually i tried to make it encrypt/decryptallselectedfile,instead ofusing $1 wewilluse$NAUTILUS_SCRIPT_SELECTED_FILE_PATHSbut the problemi faced iswhenthename include spaces, i was unableto filter spacesforsomeunknowreasons :( i tried 
```

$files=`echo -e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS | sed -e "s/ /\\\ /g"`

```
and many other things around sed, but without anysuccess,ifyoucanfilter spaces i already made the script remember thekeyforallfilesto descypt...
 
any suggestions?.[/quote]
None at the moment... I'll get back to you. I've got a couple of ideas to bounce off you when I have more time. Thanks for the input!

---

### Post by robert_pectol on 2006-01-02
[quote=meborc]REPORTING BUGS:
 
i ran a test trying to encrypt and decrypt files both on the **linux** partition and mounted **fat32** partition. here are the bugs found:
 
1) the script managed to delete the mother-file [COLOR=Red]only[/COLOR] on the **linux** partition, on the **fat32**thefileremained...maybethebug can't be fixed, if so it should bestatedinthe beginningoftheprocess, so the user is alerted of thishappening
 
2) when hitting **cancel** instead ofinsertingadecryptionkeyanerror message like in the first picture popsup... itisnotthatkind ofthing u want to see if u aredecryptingimportantdocuments:)there should be a normal rollback - cancel means that the user does notwish to decrypt the file, therefore the script should end
 
3) the errormessage that pops up,when user triestomakemorethanonecopy of the encrypted file, is alsequiteannoying(thesecondpic)...maybe the script could make a newencryptedfilecalled **encryptedfile2** or **encryptedfilecopy**
 
otherwise i find the script OK... ofcourse haven't done much testing yet :)
 
keep on the good work[/quote]
Thanks for checking it out for me! I've taken some time to go over each one of these issues to verify and/or make appropriate changes to the script. Follows are my results:
 
**Issue 1 - Non deletion of original file on fat32 filesystem:**
I couldn't reproduce this behavior on my fat32 device. The files were created/deleted as expected. Regardless, I've added an after deletion check on the file which more accurately reports the results to the user. That way the user is at least aware of whether or not it truly got deleted.
 
**Issue 2 - Handling of user selecting 'cancel' during file decryption:**
Good call! ;)  I've coded better handling of it with more applicable user feedback.
 
**Issue 3 - Handling of already existing encrypted filename:**
Another good call!  ;)  I've added the ability of the user to overwrite the file or cancel the operation, and get meaningful feedback from the UI.
 
I've replaced the script in the post a few posts above this one, which contains all of these fixes. Unless anyone finds any other issues with it, I'll go ahead and make it the official version shortly.

---

### Post by robert_pectol on 2006-01-02
[quote=souled]Awesome script. Is there any way to encrypt directories using this method?[/quote]
Not at the moment.  However, that ability might get added soon!  ;)  The current priority (other than squashing bugs) is the addition of the script's ability to allow the user to select from any of the keys on his/her keyring!  That way, users will be able to encrypt files to other users' public keys!

---

### Post by curtis on 2006-01-02
Well done on your script.
I like it a lot :D

---

### Post by Gandalf on 2006-01-03
> **robert_pectol]Ok folks, here's the new version! It now has theabilitytosecurelydelete the original file once this scripthassuccessfullyencryptedit. The option is disabled by default but canbeeasilyenabled bysetting the, "remove_orig_file" option near the topofthescript from,"no" to, "yes." **BE WARNED - With this option active, the original file will be securely deleted!**Thatmeanstheonly way to recover the original file would betosuccessfullydecrypt it!Make sure you understand that. If youenablesecure filedeletion, itmight be a good idea to test it out onanunimportant fileso that you cansee how it works.
 
This new feature requires the 'wipe' command lineutility.Itcaneasily be downloaded and installed by opening a shellandtyping,"sudoapt-get install wipe" at the command prompt.
 
Since the script has undergone many changes inordertoincorporatethis new functionality, there might be some newbugs!Pleasereportthem so that I can get them fixed.
 
 
 
[COLOR=Red]**UPDATED:[COLOR=Black] (02 Jan 2006 @2330 Z)  This latest version contains a few minor bugfixes![/COLOR]**[/COLOR]
 
 
```

#!/bin/bash
#
#  Nautilus file encryption/decryption script v2.1 - Uses GnuPG
#  Written by Robert Pectol, January 2006 - http://rob.pectol.com
#
#  This encrypter/decrypter script  must be called from Nautilus!  It
#  relies on environment variables only available from within Nautilus.
#  Place this script in your  nautilus-scripts directory and make sure
#  it's executable  (chmod 775 this_script.sh)  and it will show up in
#  the, "Scripts" menu when  files are right-clicked  from within your
#  Nautilus file manager.  Please report any bugs to rob@pectol.com.
#
#  This script requires GnuPG for file the encryption/decryption.  It
#  is usually installed by  default on most  distributions.  However,
#  you may need to generate a key pair for your user account.  This is
#  easily accomplished by opening a shell and typing the following at
#  the command prompt:  "gpg --gen-key"  (Do *NOT* use sudo for this)
#  Once you have generated your keypair, you can start encrypting and
#  decrypting files with your key, using this script!  It's important
#  to NOT forget your passphrase or your encrypted files will be that
#  way forever!!!  If you enable the secure file deletion option, then
#  you need to make sure the wipe utility is available on your system.
#  If you don't have wipe, you can easily install it by opening a shell
#  and  typing, "sudo apt-get install wipe" at the  command  prompt.
#
#  This  program is free  software.  It  is distributed  in the hope
#  that it will be useful, but WITHOUT ANY WARRANTY said:**
> ; then
        files_path=$HOME"/Desktop"
else
        files_path=`echo"$NAUTILUS_SCRIPT_CURRENT_URI" | sed -e 's/^file:\/\///; s/%20/\ /g'`
fi
gui=`which zenity`
enc_dec=`which gpg`
secure_delete=`which wipe`
 
# Secure file deletion disclaimer
agreed=`cat ~/.enc_dec_agreed` &> /dev/null
if [[ "$remove_orig_file" == "yes" && "$agreed" != "yes" ]]; then
        dialog_title="Disclaimer!"
        dialog_type="--question"
        ackn1="By activating the secure file deletion feature, you acknowledge"
        ackn2="that you understand the following:  Once the file is successfully"
        ackn3="encrypted to a new file, the original un-encrypted file will be"
        ackn4="securely deleted!  That is, it will be destroyed!  After that,"
        ackn5="the only hope of recovering the original file will be in the"
        ackn6="successful decryption of the encrypted one!  Don't forget your"
        ackn7="passphrase or your encrypted files will be that way forever!"
        ackn8="You also acknowledge that you absolve the author of this script,"
        ackn9="of any responsibility for accidental data loss due to your use of it."
        ackn10="You also acknowledge that you assume full responsibility for any and"
        ackn11="all data loss due to your use of it!  Select, 'Ok' to acknowledge."
        ackn12="(NOTE: This noticewill only be shown once unless you decline to acknowledge!)"
        feedback=`echo $ackn1$ackn2$ackn3$ackn4 $ackn5 $ackn6 $ackn7 $ackn8 $ackn9 $ackn10$ackn11$ackn12`
        zenity --title "$dialog_title" "$dialog_type" --text "$feedback"
        if [ "$?" == "0" ]; then
                echo "yes" > ~/.enc_dec_agreed
               $gui--title"Enabled!" "--info" --text "Secure file deletion is nowactive!You may now re-launch the script!"
        else
               $gui--title"Disabled!" "--info" --text "Then you should disablesecurefiledeletion before using this script again!"
        fi
        exit 0
fi
 
# Decrypt function
decrypt()
{
        # Collect GnuPG passphrase and decrypt the file
        getpasswd=`$gui  --title "GnuPG Decrypter" --entry --hide-text \
        --text="Please enter your GnuPG passphrase to decrypt $the_file:" \
        | sed 's/^[ \t]*//;s/[ \t]*$//'` &> /dev/null
        if [ "$getpasswd" == "" ]; then
                dialog_title="Operation Aborted!"
                dialog_type="--info"
               feedback="No passphrase submitted.  Operation cancelled!"
                feedback
                exit 0
        fi
        echo $getpasswd | $enc_dec-v--batch --passphrase-fd 0 --output /tmp/decrypted_output_file.dec \
        --decrypt "$files_path/$the_file" &> /tmp/encdecresult
       orig_filename=`cat/tmp/encdecresult| grep "original file name" |cut -d '=' -f2 | sed's/'\''//g'`
        mv /tmp/decrypted_output_file.dec "$files_path/$orig_filename"
        result=`cat /tmp/encdecresult | sed 's/<//g;s/>//g' | uniq`
        rm -f /tmp/encdecresult
 
        # Remove encrypted file after decryption
        if [[ "$remove_orig_file"=="yes"&& `echo "$result" | grep "decryption failed"` == ""]];then
               # Checkforexistence of the newly decrypted file before we remove theencryptedone
               if [ -O "$files_path/$orig_filename" ]; then
                       rm -f "$files_path/$the_file"
                fi
        fi
 
        # User feedback
        if [[ `echo "$result" | grep "decryption failed"` != "" ]]; then
                dialog_title="Decryption Error!"
                dialog_type="--error"
                feedback=$result
                feedback
        else
                dialog_title="Decryption Results"
                dialog_type="--info"
                if [ "$verbose" == "yes" ]; then
                     feedback="Success! - $the_file was decryptedto$orig_filename usingkey $result"
                else
                     feedback="Success! - Decrypted to $orig_filename!"
                fi
                feedback
        fi
}
 
# Encrypt function
encrypt()
{
        if [ -a "$files_path/$the_file.gpg" ]; then
                dialog_title="Confirm File Replace!"
                dialog_type="--question"
              feedback="Encrypted file for $the_file already exists! Overwriteit?"
                feedback
                if [ "$yesorno" == "1" ]; then
                       dialog_title="Operation Aborted!"
                       dialog_type="--info"
                       feedback="Cancelled!"
                       feedback
                       exit 0
                else
                       rm -f "$files_path/$the_file.gpg"
                fi
        fi
        $enc_dec -v--batch--default-recipient-self -e "$files_path/$the_file"&>/tmp/encdecresult
        result=`cat /tmp/encdecresult`
        rm -f /tmp/encdecresult
        result=`echo $result | tail -n 1 | cut -d '"' -f2 | sed 's/<//g;s/>//g'`
 
        # Remove original file (if secure file deletion is enabled)
        if [[ "$remove_orig_file"=="yes"&& `echo "$result" | grep "encryption failed"` == ""]];then
                sec_file_del
        else
               if [[ `echo "$result" | grep "encryption failed"` == "" ]]; then
                       if [ "$verbose" == "yes" ]; then
                             warn1="*WARNING*Although$the_file was encrypted to $the_file.gpg,"
                             warn2="the original filewasNOT deleted.  It is still on yourdrive!"
                             warn3="This may be asecurityissue!  Consider enabling securefile"
                             warn4="deletion.  Tostopseeing this warning, you can set theverbose"
                             warn5="option to, 'no' nearthetop of the script."
                             result=`echo "$result -$warn1$warn2 $warn3 $warn4 $warn5"`
                       fi
                fi
        fi
 
        # User feedback
        if [[ `echo "$result" | grep "encryption failed"` != "" ]]; then
                dialog_title="Encryption Error!"
                dialog_type="--error"
                feedback=$result
                feedback
        else
                dialog_title="Encryption Results"
                dialog_type="--info"
                if [ "$verbose" == "yes" ]; then
                     feedback="Success! - $the_file was encryptedto$the_file.gpg using key$result"
                else
                     feedback="Success! - Encrypted to $the_file.gpg."
                fi
                feedback
        fi
}
 
# Secure file deletion function
sec_file_del()
{
        # Check for secure file deletion utility
        if [ -x "$secure_delete" ]; then
               # Checkforexistence of the newly encrypted file before we remove theoriginal
               if [ -O "$files_path/$the_file.gpg" ]; then
                       $secure_delete -q -f "$files_path/$the_file"
                       if [ -a "$files_path/$the_file" ]; then
                             result=`echo "$result -*NOTE*$the_file (the original file) could NOTbe securely deleted!"`
                       else
                             result=`echo "$result -*NOTE*$the_file (the original file) wassecurely deleted!"`
                       fi
                fi
        else
               warn1="*WARNING* $the_file could NOT be securely deleted!"
               warn2="Make sure you have installed the wipe utility."
               warn3="(ex: 'sudo apt-get install wipe')"
               result=`echo "$result - $warn1 $warn2 $warn3"`
        fi
}
 
# Feedback function
feedback()
{
        $gui  --title "$dialog_title" $dialog_type --text="$feedback"
        yesorno=$?
}
 
# Errors function
errors()
{
        if [ -x "$gui" ]; then
               $gui --title"Error!" --error --text="Could NOT find GnuPG!"&>/dev/null
        else
                echo "Could NOT generate dialog!"
        fi
        exit 1
}
 
# Check for required tools
if [[ -x "$gui" && -x "$enc_dec" ]]; then
        if [[ "$the_file" =~ "\.gpg$" || "$1" =~ "\.pgp$" ]]; then
                decrypt
        else
                encrypt
        fi
else
        errors
fi
exit 0

```
Enjoy!  :)
You might want to review the code u've pasted, some spaces are wiped so the script is not working, look at for example
```

               $gui--title"Enabled!" "--info" --text "Secure file deletion is nowactive!You may now re-launch the script!"

```
no spaces between $gui and --title -> script is not working
btw i noticed serval times that when u post spaces are wiped :o look at your post number 31, you quoted my post number 29 but some words have spaces wiped :o

---

### Post by robert_pectol on 2006-01-03
Yeah, the damn editor keeps doing that to me!  The best bet is to simply wget the script from:  [http://rob.pectol.com/myscripts/encryption.sh.txt]("http://rob.pectol.com/myscripts/encryption.sh.txt")

I'll try and re-paste the code in the other post.  Thanks for pointing it out!

---

### Post by Gandalf on 2006-01-03
ok got it thx

i've tried it now, and here's a few notes:
[list=1]
[*]you should instead of using one (remove_orig_file="no"	# "yes" or "no") you might want to seperate it into 2, personaly i want to securely remove original file but i don't want to move the encrypted one to the trash can afterwards, so splitting it would be a wise decision
[*]When trying to encrypt a file that is not on normal mounted partition ( i.e NFS partition ) nautilus will not pass any parameters so your $the_file variable will be empty, but the envirements variables will still exist, so your $files_path is correct, the result is an error message warning about encrypting a folder and the operation is not done, you might want to switch to envirement variables so it will work on other partitions type as well
[/list]

Voil&#224;, Good Work again!

---

### Post by robert_pectol on 2006-01-03
Duly noted!  Thanks for the suggestions.  I'll address them shortly.

---

### Post by meborc on 2006-01-03
ok, tested the script on dapper - runs fine

bugs i have (and probably are in breezy too):

1) the deletion in **FAT32** still doesn't work, maybe it is my problem, but as i run dapper in original settings, so do a lot of people, and that makes it a bigger problem :D 

2) there is a possible security problem. if i encrypt a file called **test** and do not delete it, then change the contents of the motherfile (but save it still under the same name) and then try to decrypt the **test** i made from the original (now the deletion option turned ON), the encrypted file will be deleted and the original **test** will overwrite the changes i made to the motherfile in between... ok, i hope you get my point... there should be a question when there is a file named as the motherfile and the script wants to overwrite it... it shouldn't be done silently


otherwise - it looks better and better... it is really hard to find anything to improve :D

---

### Post by linkunderscore on 2006-01-03
this is pretty sweet. I don't really have much information that I would really NEED to encrypt but its a good script nonetheless. I can use it for my gaim logs and pretend I'm a spy protecting the noc list from evil communist hackers!!

---

### Post by robert_pectol on 2006-01-04
[quote=Gandalf]you should instead of using one (remove_orig_file="no" # "yes" or "no") you might want to seperate it into 2, personaly i want to securely remove original file but i don't want to move the encrypted one to the trash can afterwards, so splitting it would be a wise decision[/quote]
Done!  Check out the new version.
[quote=Gandalf]When trying to encrypt a file that is not on normal mounted partition ( i.e NFS partition ) nautilus will not pass any parameters so your $the_file variable will be empty, but the envirements variables will still exist, so your $files_path is correct, the result is an error message warning about encrypting a folder and the operation is not done, you might want to switch to envirement variables so it will work on other partitions type as well[/quote]
Interesting!  I'll look into it although it may take some time to setup a proper testing scenerio here to reproduce this.  I'll post back one way or the other and let you know the outcome.
[quote=meborc]ok, tested the script on dapper - runs fine
 
bugs i have (and probably are in breezy too):
 
1) the deletion in **FAT32** still doesn't work, maybe it is myproblem, but as i run dapper in original settings, so do a lot ofpeople, and that makes it a bigger problem :D [/quote]
I still cannot reproduce this particular problem here with my setup.  It seems to work as expected with my fat32 external hard drive.  Can anyone else verify this issue with their hardware?  If so, please let me know.
[quote=meborc]
2) there is a possible security problem. if i encrypt a file called **test**and do not delete it, then change the contents of the motherfile (butsave it still under the same name) and then try to decrypt the **test** i made from the original (now the deletion option turned ON), the encrypted file will be deleted and the original **test**will overwrite the changes i made to the motherfile in between... ok, ihope you get my point... there should be a question when there is afile named as the motherfile and the script wants to overwrite it... itshouldn't be done silently[/quote]
I've added the ability of the script to detect the existence of a file with the same un-encrypted name.  It now gives you the option to overwrite it, or cancel the operation.
[quote=meborc]
otherwise - it looks better and better... it is really hard to find anything to improve :D[/quote]
With all this excellent feedback, it's bound to get better!  :)

---

### Post by meborc on 2006-01-04
i mount my fat32 partition every time i boot up... i'm kind of lazy (i actually havent fount the best solution for doing it automatically)... i do it like this```
auso mount /dev/hda5/ /media/fat32/ -t vfat o- umask=000
```and now if i run your script in the /media/fat32/ folder, the script is unable to delete the files if asked...

it would be best to make the script check if the file was deleted or not... since i got no warning that the file deletion failed... 

cheers :D

---

### Post by robert_pectol on 2006-01-04
[quote=meborc]...it would be best to make the script check if the file was deleted or not... since i got no warning that the file deletion failed... 
 
cheers :D[/quote]
Done!  It should now let you know if the file wasn't successfully deleted.  I also coded some checks to see if file replacement succeeded or not after being prompted to overwrite existing files when they are detected.  That way you know whether or not, you have the latest encrypted or decrypted version of the file.  Let me know what you think.

---

### Post by Gandalf on 2006-01-04
[QUOTE=meborc]i mount my fat32 partition every time i boot up... i'm kind of lazy (i actually havent fount the best solution for doing it automatically)... i do it like this```
auso mount /dev/hda5/ /media/fat32/ -t vfat o- umask=000
```and now if i run your script in the /media/fat32/ folder, the script is unable to delete the files if asked...

it would be best to make the script check if the file was deleted or not... since i got no warning that the file deletion failed... 

cheers :D[/QUOTE]
Off-Topic:
Open /etc/fstab with your favorite editor and add
```

/dev/hda5       /media/fat32     vfat     defaults,iocharset=utf8,umask=000    0    0

```

and ur fat will be mounted on boot time








@Robert cool man, this script is getting better and better as u said :D good work

---

### Post by robert_pectol on 2006-01-04
Version 2.4 is posted and also available via the URL listed on the first post.  It now requires the wipe command line utility regardless of whether or not you enable the secure file deletion feature.  The reason for this is that the script initially saves the decrypted file to a temporary file so that it can get the results of the operation to decide whether or not it decrypted the file successfully.  Once the operation is deemed a success, the file is moved to the correct name/location.  In order to securely delete the temporary file created during script execution, wipe is required.  I didn't want it leaving any unencrypted file fragments laying around even if they were 'deleted!'  Anyway, it's much more secure now in how it handles those unencrypted files.

---

### Post by meborc on 2006-01-05
hey, i dont know what you changed in the script, robert, but now it works also in my fat patrition... and before you ask, i tested it before changing the fstab... so i guess there was something in the script :) ... but now everything works just fine...

gandalf - tks mate... i was hoping to find a easy solution and this worked out great

---

### Post by Mustard on 2006-01-05
Script is looking great. :)

I think it would be good to include in the opening post what packages need to be downloaded to have this script function ie wipe.

---

### Post by robert_pectol on 2006-01-05
[quote=meborc]hey, i dont know what you changed in the script, robert, but now it works also in my fat patrition... and before you ask, i tested it before changing the fstab... so i guess there was something in the script :) ... but now everything works just fine...[/quote]
I did make some changes to how the files were handled during script execution so that's probably what solved the issue.  Anyway, glad to hear it! :D 
[quote=Mustard]Script is looking great. :) 

I think it would be good to include in the opening post what packages need to be downloaded to have this script function ie wipe.[/quote]
Done!  Thanks for the suggestion.

---

### Post by fabs0028 on 2006-01-05
Thanx a lot it is a great script :)
Easy to use and really useful :)

Maybe you should think about publishing it on  [the nautilus script website]("http://g-scripts.sourceforge.net/index.php") as it could be uselful to a lot of people :)

---

### Post by meborc on 2006-01-05
i second that :) ... but it seems there is no right place for such a script... there should be a folder for file safety scripts... but i believe a lot of people would use it and right now it seems that the script is out of beta testing and ready for masses :D

---

### Post by Gandalf on 2006-01-05
Guys, do
```

sudo apt-get install seahorse

```

then just right click a file ;) it has it's pros and cons too
pros : 
[list]
[*]U can select which key to use, search between them etc...
[*]U can actually create a spereated .sig file
[*]U can encrypt/descypt any file located on Local/SSH/NFS/Samba etc... mounted partition
[/list]
cons : 
[list]
[*]Robert's Script can wipe the original while this one can't, maye we can complete it with a little nautilus script to wipe the file
[/list]

But i still beleive Robert can make this script wonderfull as he already made many features and improvements, u can also take some ideas from seahorse as zenity can be a very good tool to choose which key to use!!

---

### Post by i3dmaster on 2006-01-05
This is very cool! Thanks so much for you effort! I'd wish there is a CLI version of this so that it can be integrated into other automations... It would potentially used for production environment.

---

### Post by robert_pectol on 2006-01-06
[quote=i3dmaster]This is very cool! Thanks so much for you effort! I'd wish there is a CLI version of this so that it can be integrated into other automations... It would potentially used for production environment.[/quote] It would be trivial to pass in the required parameters from the CLI, other scripts, etc. Only 2 external vars are required to make this script function.. the filename, and the file path. The filename is already collected from $1. The first if...then...else statement could be replaced with the variable, 'files_path' being assigned to the contents of $2. Feel free to experiment with it! ;)

---

### Post by Pretzal on 2006-01-06
sorry but I can get this to work. I got the virus scan script to work no probs (thanks it's great) but I get errors with this one:

gpg: failed to creat temporary file /home/username/.gnupg/.# ****: permission denied gpg cant allocate lock for '/home/username/.gnupg/secring.gpg' gpg:keyblock resource...failed to create temporary file....general error gpg: no valid addressees....encryption failed:no such user id.

Any suggestions on what I've done or havent done?

Thanks,

---

### Post by ephman on 2006-01-06
hi,

i'm getting just a little bit of a different error then pretzal above:

gpg: no valid addressees gpg: /home/ephman/Desktop/Document: encryption failed: no such user id

i'm sure i setup gpg properly i have both keys and know my paraphrase.  any ideas would be great.

thanks for the bandwidth,
ephman

---

### Post by robert_pectol on 2006-01-07
[quote=Pretzal]gpg: failed to creat temporary file /home/username/.gnupg/.# ****: permission denied gpg cant allocate lock for '/home/username/.gnupg/secring.gpg' gpg:keyblock resource...failed to create temporary file....general error gpg: no valid addressees....encryption failed:no such user id.

Any suggestions on what I've done or havent done?

Thanks,[/quote]
Make sure that the directory ~/.gnupg exists, that you own it, and that your account has a keypair.  Other than that, I've no suggestions.  I haven't seen that error before!
[quote=ephman]gpg: no valid addressees gpg: /home/ephman/Desktop/Document: encryption failed: no such user id

i'm sure i setup gpg properly i have both keys and know my paraphrase. any ideas would be great.

thanks for the bandwidth,
ephman[/quote]
Make sure that you have created a keypair for the account under which you are **logged in**. This script tries to use the 'default' key for the user performing the operation. If it fails to find a key, for whatever reason, then it will give errors. You can list what keys are available by doing, "gpg --list-keys" at the command prompt. Usually the first key listed is your default key. Good luck!

---

### Post by Pretzal on 2006-01-07
I had a look, I do have the directory but it says in the permissions tab that I am not the owner. How do I change this?

I also tried to list the keys and came up with a very similar error.

---

### Post by robert_pectol on 2006-01-07
[quote=Pretzal]I had a look, I do have the directory but it says in the permissions tab that I am not the owner. How do I change this?

I also tried to list the keys and came up with a very similar error.[/quote]
Sounds like you did a non-standard install of GnuPG or something...
Anyway, to make yourself the owner of that dir, open a shell and type, "sudo chown -R username.username ~/.gnupg" and that should do it.  This will also give you ownership of all the files located within your .gnupg dir as well, which is required.  Good luck.

---

### Post by ephman on 2006-01-07
[QUOTE=ephman]hi,

i'm getting just a little bit of a different error then pretzal above:

gpg: no valid addressees gpg: /home/ephman/Desktop/Document: encryption failed: no such user id

i'm sure i setup gpg properly i have both keys and know my paraphrase.  any ideas would be great.

thanks for the bandwidth,
ephman[/QUOTE]


ok ok i had the the keys associated with root.  thanks for the help.

ephman

---

### Post by Pretzal on 2006-01-07
thanks robert that now works...gnupg was already installed when I tried to get this script working. I also had to redo the gpg key as I must have done that with a sudo too. Incidentally how do you remove a key as i think I have 3 now and the first one I used I would like to remove. Once again thanks for the help.

---

### Post by robert_pectol on 2006-01-08
[quote=Pretzal]thanks robert that now works...gnupg was alreadyinstalled when I tried to get this script working. I also had to redothe gpg key as I must have done that with a sudo too. Incidentally howdo you remove a key as i think I have 3 now and the first one I used Iwould like to remove. Once again thanks for the help.[/quote]
Yeah.  It's important to generate the keypair as the user, NOT as root.  Anyway, I'm glad you got it squared away!

In order to remove keys, you'll need to list the keys (gpg --list-keys) so that you can get the key IDs for the ones you want to delete.  Then use the --delete-keys, and --delete-secret-keys commands with the key IDs to purge them from your keyring.

---

### Post by monotux on 2006-01-08
[QUOTE=robert_pectol]As promised, here's my file encrypter/decrypter script for Nautilus. It's a work in progress and could use more "polishing" but it seems to get the job done! Please let me know if you have any issues with it. I tried to cover most of the bases but you know how software is. Anyway, knock it around and feel free to give me some feedback on it.
 
[COLOR=Red]***NOTE [COLOR=Black]- Updated on Jan. 4th to include a couple of minor bugfixes and some new features. It now has better, more configurable secure file deletion![/COLOR]**[/COLOR]

This script requires 3 utilities (2 of which are almost always already installed by default).
1. Zenity - Used to generate the user interface dialogs, etc. (more than likely already installed)
2. GnuPG - Does the actual encryption/decryption (more than likely already installed)
3. Wipe - Handles the secure file deletion (you'll probably need to apt-get this --> "sudo apt-get install wipe")
The latest version can always be downloaded here if the above didn't get pasted properly:
[http://rob.pectol.com/myscripts/encryption.sh.txt]("http://rob.pectol.com/myscripts/encryption.sh.txt")
 
Enjoy![/QUOTE]Thank you very much - this script is very handy! :)

---

### Post by Mustard on 2006-01-18
I was pretty impressed with this script so I tried my hand at writing my own script using zenity.  I wrote a simple nautilus script to securely delete a single file with a confirmation dialog.  I borrowed a few elements of your script, rob.  Thanks for the inspiration. :)

---

### Post by robert_pectol on 2006-01-19
You're certainly welcome! :)  I too, have written a secure file deletion script for Nautilus but haven't posted it yet.  I probably will as soon as I get a chance.  It is also based on my work with the encrypter/decrypter script.

I've also been working on adding multiple key functionality to the Nautilus file encrypter/decrypter script.  I'd like to include the ability to select from any of the keys on your keyring, for encrypting files.  That way, you could obtain others' public keys and encrypt files to them, that only they would be able to decrypt!  I'll be working on it over the next few days/weeks in my spare time but since I'm working 84 hours/week with absolutely zero days off, for the next few months, my spare time is nearly non-existant!  Anyhow, take care.

---

### Post by ice60 on 2006-01-19
thanks, robert. your scripts are really good and useful.

---

### Post by whitefort on 2007-04-09
> **robert_pectol said:**
> 
This script was written to perform operations on a single file.  If you need to encrypt a whole directory with subdirs etc., that functionality can easily be added.  If there's enough interest in that ability, let me know and I'll try and take some time to code it into the script.

I've only just discovered this script and I think it's totally wonderful - To make it perfect for me, it would just need that ability to encrypt a whole directory.

I was going to post a 'Thank you' anyway, but since I'm here, I'll also register my interest in that 'whole directory' function.  :)

Many thanks for this!!

---

### Post by DapperMe17 on 2007-10-21
Hi Robert,

Just wondering if this script will work with Xubuntu Edgy, which uses Thunar?


Thanks!

---

### Post by robert_pectol on 2007-10-28
I'm not familiar with Thunar but I'd guess probably not as is.  Does Thunar even have support for add-on scripts?  If so, then it would only be a simple matter of tweaking to get it to work.

---

### Post by ice60 on 2007-10-28
nautilus scripts work with thunar :)

Edit>Configure custom actions

---

### Post by EZ2NV on 2007-12-13
Sorry to resurrect an old thread, but I was wondering if this script was ever modified to include entire directories with multiple files in it as opposed to just a single file.  That would be SO helpful!  Either way, though, one kick *** script for sure!

---

### Post by Bossieman on 2007-12-14
Iam getting an error everytime I use this script

"Decrypted file for Skärmbild.png.gpg already exists!  Overwrite it?"

Even though the file doesny exist. Very strange. Please help

---

### Post by robert_pectol on 2008-01-11
> **Bossieman said:**
> Iam getting an error everytime I use this script

"Decrypted file for Skärmbild.png.gpg already exists!  Overwrite it?"

Even though the file doesny exist. Very strange. Please help

I don't have a Gutsy machine with which to test the latest changes, but give the most recent version a try and let us know if it is working better for you.

[QUOTE=EZ2NV]
Sorry to resurrect an old thread, but I was wondering if this script was ever modified to include entire directories with multiple files in it as opposed to just a single file. That would be SO helpful! Either way, though, one kick *** script for sure![/QUOTE]

Not yet.  But I will try to get it in the next version when I get some time to do it.

---

### Post by Ziggy72 on 2008-01-11
:KS:KS Thank you. Very nice indeed! :KS:KS

---

### Post by bharris25 on 2008-01-16
Might be a noob question but how do you decrypt the file, I have the file encrypted but there must be a different step I don't know about to decrypt because when I run the script it just encrypts the file again.

---

### Post by kevdog on 2008-01-16
I havent even downloaded this script -- so I apologize if Im way off.  But it seems like if a directory or group of files wanted to be encrypted, it would be best first to create a tar.gz archive (or you could use bzip2 for more efficient compression), and then encrypt the resultant file.  Hence the only addition to this script would be to create the archive, and then the gpg encryption would only need to work on the resultant file.

---

### Post by robert_pectol on 2008-01-16
I'm working on improving the script but in process, I introduced a small bug that I haven't had time to work out yet.  Therefore, I have removed it from my Website until I can get it resolved.  Yes, this new version has the ability to archive, compress, and encrypt whole directories!

---

### Post by robert_pectol on 2008-01-16
Latest version v3.0 available now.  It *may* still contain bugs but appears to be working well here (at least on Feisty).  It now has the ability to encrypt whole directories.  If you decide to use this script, test it out first, on a test file or directory that doesn't contain any important data so that you can be sure it's working the way you want.  Enjoy!

[http://rob.pectol.com/myscripts/encryption.sh.txt](http://rob.pectol.com/myscripts/encryption.sh.txt)

---

### Post by The Devil Is A Squirrel on 2008-01-17
> However, you may need to generate a key pair for your user account.

Hmm...I would like to have a symmetric option without any key/signing...like [here]("http://gpgee.excelcia.org/"). Just encryption.

However, thank you for your great script!! :)

---

### Post by Mustard on 2008-03-11
Just a note to Robert that I'm still using this script many years after I first saw this thread.  I recently came back to it because I noticed that this website [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php) was still using the 2.4 version of the script, whereas I was using the 2.5 version.  I have since used the link in this thread to update to the 3.0 version.  Thanks again for the script, Robert.

---

### Post by Hermesthebear on 2008-11-03
Hi guys I'm kinda new here and to Ubuntu. To begin, I'm sorry for reviving an old thread. I pretty clueless on how to start (it took me like 20 mintues to find the .gnome2/nautilus-scripts folder) I was wondering if there was a step by step for those who are new to all aspects of ubuntu. I've tried making the file executeable but keep getting this


```
chmod: cannot access `hermes/.gnome2/nautilus-scripts/file.txt': No such file or directory

```


I still feel like Im messing alot  to do though :confused:

---

### Post by lance bermudez on 2009-08-18
$ gpg --gen-key
that is what i put in terminal now what the pic shows what i get.

---

### Post by 5m0k3 on 2009-08-19
> **lance bermudez said:**
> $ gpg --gen-key
that is what i put in terminal now what the pic shows what i get.

Select option 1 if you wish to use encryption (which, is what this script does).

---


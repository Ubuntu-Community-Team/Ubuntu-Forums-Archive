---
title: "Linux -&gt; Solaris, BASH script woes"
date: 2016-04-22
forum: Programming Talk
---

### Post by deadline527gmail. on 2016-04-22
So I have a script that pulls information from a list, like hostname and directory, pulls files from all them directories for between specific dates mentioned as command line argument, does a little more in between like checking space available, list directories where you can store data, and so on.

anyway, this script was originally written for Linux, and works fine in my dev and test environments. The issue is, our production environment is NOT Linux sadly. Its SunOS. So, because of this, some of the commands function a little differently, and unfortunately I didn't know this until the script was finished - so I wrote it easily so it works, not worrying about POSIX compliance. 

I was wondering, if anyone could help me, specifically with the way the "date" command works to format the information from 04 22 2016 to Apr 22 2016. also, the way "find" works. I may have to write a long awkward function instead that lists files, checks dates, filters out the ones that were modified between the start and end date. But I am trying to avoid that.

Here is the current working script:

```

#!/bin/bash


##############################################################

####    grab_all.sh v1.0 - Written by: Thomas Tyler       ####                          ####

##############################################################


##############################################################

#### MODIFY MAILTO IN ORDER TO RECIEVE EMAIL NOTIFICATION ####

##############################################################

MAILTO="INSERT EMAIL ADDRESS HERE"

##############################################################


NOW="$(date +%m%d%y-%H%M)"

year="$(date +%Y)"


TEMP_DIR="./temp_script/"

ARCHIVE_NAME="grab_all_logs-$NOW.tar.gz"


if [ ! -d $TEMP_DIR ]

then

   mkdir $TEMP_DIR 2>/dev/null

fi


&#12288;

parse_Files_by_Date(){

end_day_to_get="$(expr $end_day_to_get_pre + 1)"


echo "+++ Parsing files to download by date..."

cat $SERVER_LIST | while read line

do

   HOST_NAME="$(echo $line | awk '{ print $1 }')"

   LOG_FILE_LOC="$(echo $line | awk '{print $2}')"

   SSH_CMD="ssh -qn $LOGIN_NAME@$HOST_NAME"


   start_date_parse="$(date -d "$start_day_to_get $start_month_to_get $year" +%Y-%m-%d)"

   start_month_parse="$(echo $start_date_parse | awk -F- '{ print $2 }')"


   end_date_parse="$(date -d "$end_day_to_get $end_month_to_get $year" +%Y-%m-%d)"

   end_month_parse="$(echo $start_date_parse | awk -F- '{ print $2 }')"


   echo "Getting files for $HOST_NAME...$LOG_FILE_LOC..."

   ls_files="$($SSH_CMD find $LOG_FILE_LOC -maxdepth 1 -newermt $start_date_parse ! -newermt $end_date_parse -ls 2>/dev/null | awk '{ print "'$HOST_NAME'"" ""'$LOG_FILE_LOC'"" "$8" "$9" "$10" "$11" "$7}')"

   echo "$ls_files" >> $TEMP_DIR/list_pre


   cp $TEMP_DIR/list_pre $TEMP_DIR/final_download_list

   sed -i '/^$/d' $TEMP_DIR/final_download_list

done

echo ""

}


check_Space(){

echo "+++ Checking available space on destination directory..."

check_folder_dest="$(df $LOG_FILE_DEST | grep % | grep -v Filesystem | awk '{ print $3}')"

check_folder_dest_mb="$(expr $check_folder_dest / 1024)"

echo "+++ Checking total amount of logs to be copied for all folders..."

echo ""

   cat $SERVER_LIST | while read line

   do

      HOST_NAME="$(echo $line | awk '{ print $1 }')"

      LOG_FILE_LOC="$(echo $line | awk '{print $2}')"

     SSH_CMD="ssh -qn $LOGIN_NAME@$HOST_NAME"

      check_folder_src="$($SSH_CMD du -s $LOG_FILE_LOC 2>/dev/null | awk '{ print $1 }')"

      if [[ $check_folder_src != "" ]]

      then

         echo "$check_folder_src" >> $TEMP_DIR/calc_total_space

      else

         echo "*** Directory $LOG_FILE_LOC does not exist on $HOST_NAME ***"

      fi

   done

}


calculate_Total_Needed(){

calc_total_needed="$(cat $TEMP_DIR/final_download_list | awk '{ print $7 }' | paste -sd+ - | bc)"

calc_total_needed_mb_pre="$(expr $calc_total_needed / 1024 / 1024)"

calc_total_needed_mb="$(echo ${calc_total_needed_mb_pre%.*})"


if [ $calc_total_needed_mb -lt 1 ]

then

   calc_total_needed_mb="1"

fi


echo ""

echo "Total space needed for all log files to be transfered: $calc_total_needed_mb MB"

echo "Space available on $LOG_FILE_DEST: $check_folder_dest_mb MB"

echo ""

}


choice_YN(){

echo ""

echo "Would you like to continue with the copy? "

while true; do

read -p "Please hit Y to continue or N to quit: " choice

case $choice in

   [Yy]* ) echo "Proceeding with log collection..."; break;;

   [Nn]* ) exit;;

    * ) echo "Please answer Y or N.";;

esac

done

}


&#12288;

check_or_Fail(){

   HOST_NAME="$(echo $SERV_INFO | awk '{print $1}')"

   LOG_FILE_LOC="$(echo $SERV_INFO | awk '{print $2}')"

    dest_size_mb="$(expr $check_folder_dest / 1024)"


   remaining_space="$(expr $dest_size_mb - $calc_total_needed_mb)"


   if [ $calc_total_needed_mb -gt $dest_size_mb ]

   then

     echo "*** ERROR: Source files are too large to copy to $LOG_FILE_DEST ***"

     echo "*** Amount required: $calc_total_needed_mb MB ***"

     echo "*** Free space on $LOG_FILE_DEST: $dest_size_mb MB ***"

     echo ""

     df_check_avail="$(df -hm | grep -e '/amex' -e '/tmp' | awk '{ print $3" "$5 }')"

     echo "$df_check_avail" > $TEMP_DIR/df_check_avail


     while read line

     do

         space_avail="$(echo $line | awk '{ print $1 }')"

         space_avail_safe_pre="$(echo "$space_avail*0.9" | bc -l)"

         space_avail_safe="$(echo ${space_avail_safe_pre%.*})"

         fs="$(echo $line | awk '{ print $2 }')"   


         echo "FS: $fs :: Space avail: $space_avail MB :: Space avail 90%: $space_avail_safe MB"


         if [ $calc_total_needed_mb -lt $space_avail_safe ]

         then

            print_avail="$(echo $line | awk '{ print $1" ""MB"" "$2}')"

            echo "$print_avail" >> $TEMP_DIR/df_print_avail

            if [ ! -s $TEMP_DIR/df_print_avail ]

            then

               echo "*** There are no filesystems large enough to store $calc_total_needed_mb MB ***"

               echo ""

               break;

            fi

         fi

     done < $TEMP_DIR/df_check_avail

     echo ""

     echo "**** Filesystems below with sufficient space to store log files...***"

     cat $TEMP_DIR/df_print_avail

     echo ""

     exit;

  fi

}


pull_Logs(){

cat $SERVER_LIST | while read SERV_INFO

do

   HOST_NAME="$(echo $SERV_INFO | awk '{print $1}')"

   LOG_FILE_LOC="$(echo $SERV_INFO | awk '{print $2}')"

   SSH_CMD="ssh -qn $LOGIN_NAME@$HOST_NAME"


   check_folder_src="$($SSH_CMD du -s $LOG_FILE_LOC 2>/dev/null | awk '{ print $1 }')" 

   if [[ $check_folder_src != "" ]]

   then

      echo "+++ Pulling log files from $LOG_FILE_LOC for $HOST_NAME..."

      cat $TEMP_DIR/final_download_list | while read line

      do

         host_download="$(echo $line | awk '{ print $1 }')"

         log_dir_download="$(echo $line | awk '{ print $2 }')"

         file_name_download="$(echo $line | awk '{ print $6 }')"

         log_dir_name="$(echo $line | awk -F/ '{print $(NF-1)}')"

         if [[ $HOST_NAME == $host_download ]]

         then

               if [[ $file_name_download == *"$LOG_FILE_LOC"* ]]

               then

                  echo "Downloading from $HOST_NAME | $file_name_download..."

                  if [ ! -d $LOG_FILE_DEST ]

                  then

                     mkdir $LOG_FILE_DEST

                  elif [ ! -d $LOG_FILE_DEST/$HOST_NAME/ ]

                  then

                     mkdir $LOG_FILE_DEST/$HOST_NAME/

                  elif [ ! -d $LOG_FILE_DEST/$HOST_NAME/$log_dir_name ]

                  then

                     mkdir $LOG_FILE_DEST/$HOST_NAME/$log_dir_name

                  fi

                  SCP_CMD="$(scp -r $LOGIN_NAME'@'$HOST_NAME':'$file_name_download $LOG_FILE_DEST'/'$HOST_NAME'/'$log_dir_name'/' 2>/dev/null)"

                  $SCP_CMD

               fi

            

         fi

      done

   else

      echo "*** Directory $LOG_FILE_LOC does not exist on $HOST_NAME ***"

   fi

done


echo ""

echo "+++++++++++++++++++++++++++++++++++++++++++++++++++++"

echo "+++ Finished pulling log folders provided in list +++"

echo "+++++++++++++++++++++++++++++++++++++++++++++++++++++"

}


send_Mail(){

echo ""

echo "+++ Sending mail notification that transfer has completed..."

mailx -s 'Log File Download Completed' $MAILTO < $TEMP_DIR/final_download_list

}


clear_After_Archive(){

cat $TEMP_DIR/final_download_list | while read line

do

   clear_folder="$(echo $line | awk '{ print $1 }')"


   rm -rf $LOG_FILE_DEST/$clear_folder/ 2>/dev/null

done

rm $TEMP_DIR/* 2>/dev/null

}


archive_Logs(){

echo "+++ Archiving all log files in $ARCHIVE_NAME..."

echo ""

ARCHIVE="$(tar -czvf $ARCHIVE_NAME -C $LOG_FILE_DEST/ . 2>/dev/null 1>/dev/null)"

$ARCHIVE

if [ -s $ARCHIVE_NAME ]

then

     echo "+++++++++++++++++++++++++++++++++++++++++++++++++++++"

     echo "Archiving completed into file $ARCHIVE_NAME"

     echo "+++++++++++++++++++++++++++++++++++++++++++++++++++++"

     echo ""

else

     echo "*****************************************************"

     echo "***              Archiving failed.                ***"

     echo "*****************************************************"

     echo ""

fi

}


echo ""


echo "<><><><><><><><><><><><><><><><><><><><><><><><><><><"

echo "====================================================="

echo "=                Grab All Log Files v1.0              ="

echo "=             ./grab_all.sh -h for syntax           ="

echo "====================================================="

echo "><><><><><><><><><><><><><><><><><><><><><><><><><><>"

echo ""


&#12288;

if [ "$1" == "-h" ]

then

     echo ""

     echo "+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++"

     echo "+ Usage: ./grab_all.sh login_name log_save_dir serv_list start_month start_day end_month end_date  +"

     echo "+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++"

     echo ""

     exit


elif [ "$#" -ge 8 ]

then

     echo ""

     echo "****************************************************"

     echo "*         Please check syntax and try again...     *"

     echo "****************************************************"

     echo ""

     exit


elif [ "$#" == "0" ]

then

     read -p "What login name would you like to use? " LOGIN_NAME

     read -p "Where do you want to store the log files? " LOG_FILE_DEST

     if [ ! -d $LOG_FILE_DEST ]

     then

        echo ""

        echo "*** Log file destination does not exist. Would you like to create it? ***"

        while true; do

            read -p "Please hit Y to continue or N to quit: " choice

            case $choice in

               [Yy]* ) echo "Creating folder..."; mkdir $LOG_FILE_DEST; break;;

               [Nn]* ) exit;;

                   * ) echo "Please answer Y or N.";;

            esac

        done

        echo ""

     fi


     read -p "Where is the server list stored? " SERVER_LIST

     if [ ! -f $SERVER_LIST ]

     then

        echo ""

        echo "*** Log folder list does not exist. Please try again. ***"

        echo ""

        exit;

     fi

     

     read -p "Please enter your start month: " start_month_to_get

     read -p "Please enter your start day: " start_day_to_get

     read -p "Please enter your end month: " end_month_to_get

     read -p "Please enter your end day: " end_day_to_get_pre


     NUM_LOG_DIR="$(wc -l $SERVER_LIST | awk '{print $1}')"


     echo "There are $NUM_LOG_DIR folders you are about to copy from.."

     echo ""


     parse_Files_by_Date

     check_Space

     calculate_Total_Needed; 

     check_or_Fail

     choice_YN  

     pull_Logs 

     send_Mail

     archive_Logs

     clear_After_Archive

else

         LOGIN_NAME="$1"

         LOG_FILE_DEST="$2"

         if [ ! -d $LOG_FILE_DEST ]

         then

            echo ""

            echo "*** Log file destination does not exist. Would you like to create it? ***"

            while true; do

                read -p "Please hit Y to continue or N to quit: " choice

                case $choice in

                   [Yy]* ) echo "Creating folder..."; mkdir $LOG_FILE_DEST; break;;

                   [Nn]* ) exit;;

                       * ) echo "Please answer Y or N.";;

                esac

            done

            echo ""

         fi

         SERVER_LIST="$3"

         if [ ! -f $SERVER_LIST ]

         then

            echo ""

            echo "*** Folder list does not exist. Please try again. ***"

            echo ""

            exit;

         fi

         start_month_to_get="$4"

         start_day_to_get="$5"

         end_month_to_get="$6"

         end_day_to_get_pre="$7"

         parse_Files_by_Date

         check_Space

         calculate_Total_Needed

         check_or_Fail

         pull_Logs

         send_Mail

         archive_Logs

         clear_After_Archive

fi


```

---

### Post by T.J. on 2016-04-22
I wish I could help you with greater detail, but it has been a very long time since I did anything with SunOS or Solaris.  I can only offer my moral support, and the suggestion that perhaps the man pages on SunOS might provide the details for the date command  that you require.

[http://www.manpages.info/sunos/date.1.html](http://www.manpages.info/sunos/date.1.html)

This page looks old, but I think it is v5 which should be close. I'd try the console version already on your system.

---

### Post by Rocket2DMn on 2016-04-22
These problems can be difficult to solve - cross platform compatibility for shell scripting is complicated.  In some cases you can verify consistency in behavior, other times you just have to do runtime checks.  I'd also recommend that when you validate your script, you check for silent scripting errors that do not produce error messages.  E.g. the columns you print with awk may produce data on SunOS but not the fields you're actually looking for that you tested on Linux.

It's obviously best if your test environments mirror your deployment environments as closely as possible - switching operating systems and even OS versions qualifies as a pretty big difference in my book.

---

### Post by T.J. on 2016-04-23
> **Rocket2DMn said:**
> These problems can be difficult to solve - cross platform compatibility for shell scripting is complicated.  In some cases you can verify consistency in behavior, other times you just have to do runtime checks.  I'd also recommend that when you validate your script, you check for silent scripting errors that do not produce error messages.  E.g. the columns you print with awk may produce data on SunOS but not the fields you're actually looking for that you tested on Linux.

It's obviously best if your test environments mirror your deployment environments as closely as possible - switching operating systems and even OS versions qualifies as a pretty big difference in my book.

I agree, Rocket.

I realize that this is slightly OT to say this, but problems like this are the reason I am glad that ISO C code is the "lingua franca" of Unix.  Scripts have never been compatible from Unix to Unix in spite of POSIX.  I feel for Deadline. I really do - but thank the heavens for standardized C.

---


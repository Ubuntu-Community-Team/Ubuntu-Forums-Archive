---
title: "where does my script spend the most of time?"
date: 2014-11-18
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-11-18
Hi all, 

I'd like to know where does my script spend the most of time. 
Please find code below. 
I'm newbie and would like to know how do I start script debugging? 
Any suggestion is appreciated! 

```

$ less /QA/u01/oracle/admin/plsdw/plsdw_scripts/nag_pls_exec_sql_ftp.ksh
#!/bin/ksh

#**************************************************************************************************
# Script: nag_pls_exec_sql_ftp.ksh
#
#
# Description: Script to run sql commands in the Oracle database, and then transfer output files.
#
#**************************************************************************************************

export ver=v1.14

set -f  # do not substitute filenames for * (in SQL queries)


export ORAENV_ASK=NO
export PATH=/usr/bin:/usr/local/bin:/bin

HOSTNAME=`hostname|tr [:lower:] [:upper:]`

MAIN_SCRIPT_LONG=$0
MAIN_SCRIPT_SHORT=`basename $MAIN_SCRIPT_LONG|tr [:lower:] [:upper:]`

CFG_FILE=`dirname $0`/$1

. $CFG_FILE             # source cfg file
. $MAIN_ORA_PROFILE     # source main oracle profile (Oracle settings)

TS=$(date +'%Y%m%d%H%M%S')
LOCK_FILE=$LOG_DIR/$PREFIX.lck
MAIN_LOG=$LOG_DIR/${PREFIX}_main.log
DELTA_LOG=$LOG_DIR/${PREFIX}_${TS}.log
WARN_LOG=$LOG_DIR/${PREFIX}_WARN.log
SQL_SCRIPT=$LOG_DIR/${PREFIX}_${TS}_sql.sql
SQL_LOG=$LOG_DIR/${PREFIX}_${TS}_sql.log
SFTP_SCRIPT=$LOG_DIR/${PREFIX}_${TS}_sftp.sh
SFTP_LOG=$LOG_DIR/${PREFIX}_${TS}_sftp.log
CFG_ESTIM=$LOG_DIR/${PREFIX}_estim.cfg
SQL_ESTIM=$LOG_DIR/${PREFIX}_estim_sql.sql
ESTIM_FILTER=$1


notific="SUCCESS!"

sep1="======================================================================================================="

ora_avg_time_query()
{
        print "set head off"            > $SQL_ESTIM
        print "conn $DBCONN_AUDIT"            >> $SQL_ESTIM
        print " select 'ESTIM='||TO_CHAR(extract(hour   from TO_TIMESTAMP(tb.Average,'HH24:MI:SS'))*60*60+ "  >> $SQL_ESTIM
        print " extract(minute from TO_TIMESTAMP(tb.Average,'HH24:MI:SS'))*60+ "  >> $SQL_ESTIM
        print " extract(second from TO_TIMESTAMP(tb.Average,'HH24:MI:SS'))) as av_time "  >> $SQL_ESTIM
        print " from  PLS_LOG_DETAILS_MVIEW tb "  >> $SQL_ESTIM
        print " where tb.cron_job='$ESTIM_FILTER';    "  >> $SQL_ESTIM
        print "exit"                    >> $SQL_ESTIM

        sqlplus /nolog @$SQL_ESTIM | grep ESTIM > $CFG_ESTIM

        err1=$?                                         # save exit code

     #   if [ $err1 != 0 ]; then
     #        finish "SQL Average Time Failure!"
     #   fi
. $CFG_ESTIM
}

rm_files()
{
        [ -e $DELTA_LOG ]       && rm $DELTA_LOG
        [ -e $SQL_SCRIPT ]      && rm $SQL_SCRIPT
        [ -e $SQL_LOG ]         && rm $SQL_LOG
        #[ -e $SQL_QUERY_OUT ]  && rm $SQL_QUERY_OUT
        [ -e $SFTP_SCRIPT ]     && rm $SFTP_SCRIPT
        [ -e $SFTP_LOG ]        && rm $SFTP_LOG
}

init()
{

    if [ -e $LOCK_FILE ] && [ "$IS_ONLY_ONE_INSTANCE" == "1" ]; then
                if [ "$NOTIF_EMAIL" == "1" ]; then
                        st1="Script is already running. '$LOCK_FILE' found."
                        echo "$st1"|mailx -s "FAILURE! $DESC.$(hostname)." "$EMAILS"
                        if [ "$ADMIN_EMAILS" != "" ]; then
                                echo "$st1"|mailx -s "FAILURE! (admin email) $DESC.$(hostname)." "$ADMIN_EMAILS"
                        fi
                        exit 1
                fi
        fi

        touch $LOCK_FILE
        rm_files
        d1=$(date +"%D %H:%M:%S")
        d1second=$SECONDS

        print $sep1     |tee -a $DELTA_LOG
        print $(date)   |tee -a $DELTA_LOG
        print $sep1     |tee -a $DELTA_LOG

        # explicitly set flag if email must be sent in case of error only
        if [ "$EMAIL_ON_ERR_ONLY" != "1" ]; then
                EMAIL_ON_ERR_ONLY=0
        fi

        # mode is 'file' by default (all output files are described in the cfg file)
        [ "$SQL_MODE" == "" ] && SQL_MODE=file

        log_id=$(sqlplus -s /nolog <<-EOF|awk 'NR==2 {print $1}'
                set head off
                set feed off
                set pagesize 0
                conn $DBCONN_AUDIT
                select pls_audit.get_id_log from dual;
EOF)
        sqlplus /nolog <<-EOF
                conn $DBCONN_AUDIT
                exec pls_audit.log_start($log_id,\
                                        '$HOSTNAME.$MAIN_SCRIPT_SHORT.START',\
                                        'STARTED AT: $d1, $MAIN_SCRIPT_LONG $CFG_FILE, ORACLE_SID=$ORACLE_SID');
EOF
        err1=0
}

get_attachment()
{
        case $SQL_MODE in
        file)   for i in `awk '/^SFTP_FILE/ {print substr($0,10,256)}' $CFG_FILE|sort -k 1n|awk -F= '{print $1}'`
                 do
                        attach=$(eval print "\$SFTP_FILE$i"|awk '{print $1}')
                        a1=$(eval print "\$SFTP_FILE$i"|awk '{print $3}')
                        if [ "$a1" == "1" ]; then
                                print "Attachment: '$attach'"|tee -a $DELTA_LOG
                                return
                        fi
                 done
                attach=""
                print "No attachments."|tee -a $DELTA_LOG
        ;;
        query)  attach=$SQL_QUERY_OUT
                ls -la $attach
                a2=`grep -i Cell $SQL_QUERY_OUT | wc -l`
                if [ $a2 != 0 ]; then
                        print "Attachment: '$attach'"|tee -a $DELTA_LOG
                else
                        print "No attachments."|tee -a $DELTA_LOG
                        attach=""
                fi
        ;;
        esac
}

finish()
{
        notif_msg="$1 $(date +"%D %H:%M:%S").$(hostname).$DESC."

        print "$notif_msg" |tee -a $DELTA_LOG
        d2=$(date +"%D %H:%M:%S")
        d2second=$SECONDS
        printf "\nScript ($ver) worked:\n"      |tee -a $DELTA_LOG
        print "begin: $d1"              |tee -a $DELTA_LOG
        print "end  : $d2"              |tee -a $DELTA_LOG
        print $sep1                     |tee -a $DELTA_LOG
        cat $CFG_FILE >> $MAIN_LOG      # SAVE CFG FILE TO THE MAIN LOG
        cat $DELTA_LOG >> $MAIN_LOG     # SAVE SESSION LOG TO THE MAIN LOG
        if [ "$NOTIF_EMAIL" == "1" ]; then
                if [[ "$EMAIL_ON_ERR_ONLY" == "1" && "$err1" != "0" ]] || [ "$EMAIL_ON_ERR_ONLY" == "0" ]; then
                        get_attachment
                        if [ "$attach" == "" ]; then
                          if [ "$SQL_MODE" != "query" ]; then
                                cat $DELTA_LOG|mailx -s "$1 $DESC.$(hostname)." "$EMAILS"
                                if [ "$ADMIN_EMAILS" != "" ]; then
                                        cat $CFG_FILE $DELTA_LOG|
                                        mailx -s "$1 (admin email) $DESC.$(hostname)." "$ADMIN_EMAILS"
                                fi
                          fi
                        else
                                (cat $DELTA_LOG;uuencode $attach $(basename $attach))|mailx -s "$1 $DESC.$(hostname)." "$EMAILS"
                                if [ "$ADMIN_EMAILS" != "" ]; then
                                        (cat $CFG_FILE $DELTA_LOG;uuencode $attach $(basename $attach))|
                                        mailx -s "$1 (admin email) $DESC.$(hostname)." "$ADMIN_EMAILS"
                                fi
                        fi
                fi

                time_diff=$(($d2second - $d1second))
                
                if [ ! -z $ESTIM ]; then
                        SQL_PRC_GAIN=$(($time_diff*100/$ESTIM-100))
                        if [[ $SQL_PRC_GAIN -gt $SQL_WARNING_TRESHOLD_PRC ]]; then
                                print "\nActual time: $time_diff seconds \nAverage for 7 Days: $ESTIM seconds \n$SQL_PRC_GAIN% gain \n" > $WARN_LOG
                                cat $CFG_FILE $DELTA_LOG >> $WARN_LOG
                                mailx -s "SQL Warning! (admin email) $DESC.$(hostname)." $ADMIN_EMAILS < $WARN_LOG
                                rm -f $WARN_LOG
                        fi
                fi
        fi

        rm_files

        sqlplus /nolog <<-EOF
                conn $DBCONN_AUDIT
                exec pls_audit.log_end( $log_id,\
                                        '$HOSTNAME.$MAIN_SCRIPT_SHORT.$1',\
                                        'COMPLETED AT: $d2, $MAIN_SCRIPT_LONG $CFG_FILE, ORACLE_SID=$ORACLE_SID');
EOF
        rm $LOCK_FILE
        exit $err1
}

generate_xml()
{
        f1=_tmp1
        f2=_tmp2

        cat $SQL_QUERY_OUT |sed -e 's/^"//g;s/"$//g;s/","/|/g'|tr '|' '\t' > $f1

        [ -e $SQL_QUERY_OUT ] && rm $SQL_QUERY_OUT

        # prepare XML header
        while read LINE;
         do
                print $LINE >> $SQL_QUERY_OUT
         done <<EOF
<?xml version="1.0"?>
<?mso-application progid="Excel.Sheet"?>
<Workbook xmlns="urn:schemas-microsoft-com:office:spreadsheet"
xmlns:o="urn:schemas-microsoft-com:office:office"
xmlns:x="urn:schemas-microsoft-com:office:excel"
xmlns:ss="urn:schemas-microsoft-com:office:spreadsheet"
xmlns:html="http://www.w3.org/TR/REC-html40">
<DocumentProperties xmlns="urn:schemas-microsoft-com:office:office">
<Author>a</Author>
<LastAuthor>a</LastAuthor>
<Created>2013-08-18T18:36:57Z</Created>
<Company>a</Company>
<Version>11.9999</Version>
</DocumentProperties>
<ExcelWorkbook xmlns="urn:schemas-microsoft-com:office:excel">
<WindowHeight>11385</WindowHeight>
<WindowWidth>15180</WindowWidth>
<WindowTopX>360</WindowTopX>
<WindowTopY>90</WindowTopY>
<ProtectStructure>False</ProtectStructure>
<ProtectWindows>False</ProtectWindows>
</ExcelWorkbook>
<Styles>
<Style ss:ID="Default" ss:Name="Normal">
<Alignment ss:Vertical="Bottom"/>
<Borders/>
<Font ss:FontName="Arial Cyr"/>
<Interior/>
<NumberFormat/>
<Protection/>
</Style>
<Style ss:ID="s21">
<Borders>
<Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1"/>
<Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1"/>
<Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1"/>
<Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1"/>
</Borders>
<Font ss:FontName="Arial Cyr" ss:Bold="1"/>
</Style>
<Style ss:ID="s22">
<Borders>
<Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1"/>
<Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1"/>
<Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1"/>
<Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1"/>
</Borders>
</Style>
</Styles>
<Worksheet ss:Name="Sheet1">
<Table>
<Column ss:Width="50"/>
<Column ss:Width="50"/>
<Column ss:Width="50"/>
EOF
        print "<Row>"   >> $SQL_QUERY_OUT
        for i in `awk 'NR==1' $f1`
         do
                print ' <Cell ss:StyleID="s21"><Data ss:Type="String">'$i'</Data></Cell>' >> $SQL_QUERY_OUT
         done
        print "</Row>"  >> $SQL_QUERY_OUT
        awk 'NR>1' $f1|while read LINE;
         do
                print "<Row>"   >> $SQL_QUERY_OUT
                print "$LINE"|awk -F\t '{for (i=1;i<=NF;i++){print $i}}' > $f2
                while read i;
                 do
                        k=$(print "$i"|sed 's/&/&amp;/g')       # replace ampersand
                        print ' <Cell ss:StyleID="s22"><Data ss:Type="String">'$k'</Data></Cell>' >> $SQL_QUERY_OUT
                 done < $f2
                print "</Row>"  >> $SQL_QUERY_OUT
         done

        # add XML footer
        while read LINE;
         do
                print $LINE >> $SQL_QUERY_OUT
         done <<EOF
  </Table>
  <WorksheetOptions xmlns="urn:schemas-microsoft-com:office:excel">
   <PageSetup>
    <PageMargins x:Bottom="0.984251969" x:Left="0.78740157499999996"
     x:Right="0.78740157499999996" x:Top="0.984251969"/>
   </PageSetup>
   <Print>
    <ValidPrinterInfo/>
    <HorizontalResolution>200</HorizontalResolution>
    <VerticalResolution>200</VerticalResolution>
   </Print>
   <Selected/>
   <Panes>
    <Pane>
     <Number>3</Number>
     <ActiveRow>1</ActiveRow>
     <ActiveCol>2</ActiveCol>
    </Pane>
   </Panes>
   <ProtectObjects>False</ProtectObjects>
   <ProtectScenarios>False</ProtectScenarios>
  </WorksheetOptions>
 </Worksheet>
</Workbook>
EOF
        [ -e $f1 ] && rm $f1
        [ -e $f2 ] && rm $f2
}

ora_process_query()
{
        [ $err1 -ne 0 ] && return

        print "Start Oracle ..."|tee -a $DELTA_LOG
        print "Query: "         |tee -a $DELTA_LOG

        print "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~" |tee -a $DELTA_LOG
        print $SQL_QUERY                        |tee -a $DELTA_LOG
        print "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~" |tee -a $DELTA_LOG

        print "conn $DBCONN"            > $SQL_SCRIPT
        print "set feed off"            >> $SQL_SCRIPT
        print "set pagesize 0"          >> $SQL_SCRIPT
        print 'set colsep ""","""'      >> $SQL_SCRIPT
        print "set linesize 5000"       >> $SQL_SCRIPT
        print "set pagesize 5000"       >> $SQL_SCRIPT
        print "set trimspool on"        >> $SQL_SCRIPT
        print "spool $SQL_QUERY_OUT"    >> $SQL_SCRIPT
        print "$SQL_QUERY"              >> $SQL_SCRIPT
        print "exit"                    >> $SQL_SCRIPT

        sqlplus -s /nolog @$SQL_SCRIPT >> $SQL_LOG
        err1=$?                                         # save exit code

        err2=`grep -i ora- $SQL_LOG|wc -l|awk '{print $1}'` # if SQL_LOG has any ORA- errors
        if [[ $err1 != 0 || $err2 != 0 ]]; then
                finish "SQL Failure!"
        fi

        sed -e 's/[ ]*["][,]["]/","/g;s/^[ ]*/"/g;s/$/"/g' $SQL_QUERY_OUT|sed -e '3d'|sed -e '1d' > /tmp/_f1
        mv /tmp/_f1 $SQL_QUERY_OUT
        [ "$SQL_QUERY_TYPE" == "XML" ] && generate_xml
}
ora_work()
{
        [ $err1 -ne 0 ] && return
        print "Start Oracle ..." |tee -a $DELTA_LOG
        print "conn $DBCONN" > $SQL_SCRIPT
        # put all commands to Oracle database in ordered way
        for i in `awk '/^SQL_FILE/ {print substr($0,9,256)}' $CFG_FILE|sort -k 1n|awk -F= '{print $1}'`
         do
                eval print "\$SQL_FILE$i" >> $SQL_SCRIPT
         done

        sqlplus /nolog @$SQL_SCRIPT >> $SQL_LOG
        err1=$?                                         # save exit code

        print "SQL LOG:"        |tee -a $DELTA_LOG
        cat $SQL_LOG            |tee -a $DELTA_LOG      # save sql log to the main log

        err2=`grep -i ora- $SQL_LOG|wc -l|awk '{print $1}'` # if SQL_LOG has any ORA- errors
        if [[ $err1 != 0 || $err2 != 0 ]]; then
                finish "SQL Failure!"
        fi
}

save_local()
{
        [ $err1 -ne 0 ] && return
        [ "$HIST_DIR" == "" ] && return

        print |tee -a $DELTA_LOG
        print -n "Save files to the local dir ..." |tee -a $DELTA_LOG
        for i in `awk '/^SFTP_FILE/ {print substr($0,10,256)}' $CFG_FILE|sort -k 1n|awk -F= '{print $1}'`
         do
                generated_file=$(eval print "put \$SFTP_FILE$i"|awk '{print $2}')       # fullname of the generated file
                fn=$(basename $generated_file)                                          # shortname of the generated file
                history_file=${fn%%.*}_$TS.${fn##*.}            # add timestamp between name and extension
                cp -p $generated_file $HIST_DIR/$history_file   # copying
         done
        print "done." |tee -a $DELTA_LOG
}

sftp_chk()
{
        [ $ERR_IF_RMT_FILES_EXIST -eq 0 ] && return
        print |tee -a $DELTA_LOG
        print -n "Checking if output files exist on the dst host..."|tee -a $DELTA_LOG
        for i in `awk '/^SFTP_FILE/ {print substr($0,10,256)}' $CFG_FILE|sort -k 1n|awk -F= '{print $1}'`
         do
                f1=$(eval print "\$SFTP_FILE$i"|awk '{print $2}')
                res=$(ssh $SFTP_DST_HOST "ls -la $f1" 2>/dev/null|wc -l|awk '{print $1}')
                if [ $res -eq 1 ]; then
                        print -n "\nOutput file '$f1' exists on the remote host '$SFTP_DST_HOST'"|tee -a $DELTA_LOG
                        err1=1
                fi
                sleep 5 # to prevent net flood
         done
        if [ $err1 != 0 ]; then
                print |tee -a $DELTA_LOG
                print "Warning! Some output files exist on the dst host!"|tee -a $DELTA_LOG
                notific="WARNING!"
                err1=0
        else
                print "done."|tee -a $DELTA_LOG
        fi
}
sftp_work()
{
        [ $err1 -ne 0 ] && return
        [ "$SFTP_DST_HOST" == "" ] && return

        sftp_chk        # check out if files exist on dst host
        print -n > $SFTP_SCRIPT
        # put all commands to sftp utility in ordered way
        for i in `awk '/^SFTP_FILE/ {print substr($0,10,256)}' $CFG_FILE|sort -k 1n|awk -F= '{print $1}'`
         do
                eval print "\$SFTP_FILE$i"|awk '{print "put "$1" "$2}' >> $SFTP_SCRIPT
         done
        print "bye" >> $SFTP_SCRIPT

        print |tee -a $DELTA_LOG
        print "Transfer file to the destination host and dir ..." |tee -a $DELTA_LOG
        sftp -b $SFTP_SCRIPT $SFTP_DST_HOST >> $SFTP_LOG 2>>$DELTA_LOG
        err1=$?                                         # save exit code
        print |tee -a $DELTA_LOG
        print "SFTP LOG:"       |tee -a $DELTA_LOG
        cat $SFTP_LOG           |tee -a $DELTA_LOG      # save sftp log to the main log
        if [ $err1 != 0 ]; then
                finish "SFTP Failure!"
        fi
}

ftp_chk()
{
        [ $ERR_IF_RMT_FILES_EXIST -eq 0 ] && return
        print |tee -a $DELTA_LOG
        print -n "Checking if output files exist on the dst host..."|tee -a $DELTA_LOG
        for i in `awk '/^SFTP_FILE/ {print substr($0,10,256)}' $CFG_FILE|sort -k 1n|awk -F= '{print $1}'`
         do
                file1=$(eval print "\$SFTP_FILE$i"|awk '{print $2}')
                dir1=$(dirname $file1)
                print "ls $dir1"        > $SFTP_SCRIPT
                print "bye"             >> $SFTP_SCRIPT
                cat $SFTP_SCRIPT|ftp $FTP_DST_HOST > $SFTP_LOG 2>&1
                res=$(grep $file1 $SFTP_LOG|wc -l|awk '{print $1}')
                if [ $res -eq 1 ]; then
                        print -n "\nOutput file '$file1' exists on the remote host '$FTP_DST_HOST'"|tee -a $DELTA_LOG
                        err1=1
                fi
                sleep 5 # to prevent net flood
         done
        if [ $err1 != 0 ]; then
                print |tee -a $DELTA_LOG
                print "Warning! Some output files exist on the dst env!"|tee -a $DELTA_LOG
                notific="WARNING!"
                err1=0
        else
                print "done."|tee -a $DELTA_LOG
        fi
}
ftp_work()
{
        [ $err1 -ne 0 ] && return
        [ "$FTP_DST_HOST" == "" ] && return

        ftp_chk         # check out if files exist on dst host
        if [ "$FTP_TYPESET" != "" ]; then
                print "$FTP_TYPESET" > $SFTP_SCRIPT
        fi
        # put all commands to ftp utility in ordered way
        for i in `awk '/^SFTP_FILE/ {print substr($0,10,256)}' $CFG_FILE|sort -k 1n|awk -F= '{print $1}'`
         do
                eval print "\$SFTP_FILE$i"|awk '{print "put "$1" "$2}' >> $SFTP_SCRIPT
         done
        print "bye" >> $SFTP_SCRIPT

        print |tee -a $DELTA_LOG
        print "Transfer file to the destination host and dir ..." |tee -a $DELTA_LOG
        cat $SFTP_SCRIPT|ftp -v $FTP_DST_HOST > $SFTP_LOG 2>&1
        err1=$?                                         # save exit code
        print |tee -a $DELTA_LOG
        print "SFTP LOG:"       |tee -a $DELTA_LOG
        cat $SFTP_LOG           |tee -a $DELTA_LOG      # save ftp log to the main log
        # Analyze ftp log if it contains any errors
        err2=$(cat $SFTP_LOG|awk "/No such file or directory/||/Login incorrect/"|wc -l|awk '{print $1}')
        if [[ $err1 != 0 || $err2 != 0 ]]; then
                finish "FTP Failure!"
        fi
}

# Main script
init
if [ ! -z $SQL_WARNING_TRESHOLD_PRC ]; then
        ora_avg_time_query
fi
case $SQL_MODE in
        query)  ora_process_query
        ;;
        file)   ora_work
                save_local
                case $TRANSFER in
                        SFTP)   sftp_work;;
                        FTP)    ftp_work;;
                esac
        ;;
        *)      err1=1
                finish "SQL_MODE is not defined! Must be file or query."
        ;;
esac
finish $notific


(END) 


```

---

### Post by TheFu on 2014-11-18
This is generally called "profiling a program" ... different languages have different tools to accomplish this.  Googling "bash profiler" found this:
[https://stackoverflow.com/questions/4336035/performance-profiling-tools-for-shell-scripts](https://stackoverflow.com/questions/4336035/performance-profiling-tools-for-shell-scripts)
with lots of non sequitur results thanks to the .profile startup file for bash.

Use strace. [https://stackoverflow.com/questions/174942/how-should-strace-be-used](https://stackoverflow.com/questions/174942/how-should-strace-be-used)
strace is the system-level tool to profile anything. That doesn't mean it is the best answer.

---

### Post by matt_symes on 2014-11-18
Hi

I have used this in the past to profile bash and zsh scripts but it also works for ksh.

Add this to the start of your script *main execution*.

```
PS4=' $(date "+%s - %N")\011
exec 3>&2 2>./prof.$$
set -x
```

At the end of your scripts *main execution* you need to add this.

```

set +x
exec 2>&3 3>&-
```

It works by redefining the PS4 prompt. This prompt can be configured and also gets called each time a statement is run in the script.
It then redirects this prompt to the file prof.$$ where $$ is the pid of the running script.
I'm sure you know what set +-x do.
Finally it cleans up the redirect.

It also needs a hat tip to stack exchange.

Kind regards

---


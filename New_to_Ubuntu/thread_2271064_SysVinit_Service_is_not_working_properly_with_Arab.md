---
title: "SysVinit Service is not working properly with Arabic Language after reboot"
date: 2015-03-27
forum: New to Ubuntu
---

### Post by Ankit_Bajpai on 2015-03-27
I wrote a program to list down the important files and save them in a file. The files names are in different languages like English, Arabic, Hebrew etc. My program do the task properly but when i create a SysVinit Service and configure it to runlevels, my program doesn't detect the files other than English language after reboot, and it behave unexpectedly, when i restart the service which executes the program, it again detect files with all languages.
Kindly suggest what is the issue here. Becuase it only happens after reboot, when runlevels execute my service. Please let me know if it can be solved or what is the main reason behind it

---

### Post by ian-weisser on 2015-03-27
Ubuntu doesn't use sysvinit and doesn't use runlevels anymore.
Ubuntu 12.04, 14.04, and 14.10 use Upstart, which includes a limited sysvinit-like compatibility layer that lets many older initscripts still work.
Ubuntu 15.05 uses systemd instead of Upstart, but the limitations of sysvinit compatibility are about the same.

To answer your question in more specific detail, we would need to know more about the service's initscript, it's start/stop criteria, and more about the specific errors or failures.

---

### Post by Ankit_Bajpai on 2015-03-30
Initially we started with UPSTART but it failed too then we switch back to Sysvint. The Upstart was not able to list and read the arabic named file but sysvinit solved this issue when service started manually. But again this issue comes when server reboot it doesn't list and read the file. We have tried to check in other way by setting cron to execute service start on reboot and it works fine. From there we conclude it is the problem with service. (FYI : We are not using Ubuntu 15.x version)

Here is the code snippet for sysvinit service


############################################################

#!/bin/bash


CMD='CMD to execute process'
chk_PROC='process name to be checked '
chk_PROC_FIM='dependent process name to be checked '
chk_loop="0"
start() {
        PROC="$(ps -ef | grep $chk_PROC | grep -v grep | awk '{print $2}' | head -1)"
                PROC_FIM="$(ps -ef | grep $chk_PROC_FIM | grep -v grep | awk '{print $2}' | head -1)"
                if [[ -z "$PROC" && -z "$PROC_FIM" ]]; then

                                        echo "Starting PROCESS . . ."
                        ${CMD} &
                                                sleep 1
                        PROC="$(ps -ef | grep $chk_PROC | grep -v grep | awk '{print $2}' | head -1)"
                        if [ -z "$PROC" ]; then
                                                        if [[ "$chk_loop" -lt "3" ]]; then
                                                                start
                                                                chk_loop=$((chk_loop+1))
                                                        else
                                                                echo "unable to start PROCESS"
                                                                return
                                                        fi
                                                else
                                                        echo "PROCESS started, process $PROC."
                                                        return
                                                fi
                elif [ -z "$PROC" ]; then
                                        kill -9 "$PROC_FIM"
                                        start
                                else
                                        echo "PROCESS is already running, process $PROC."
                                        return
                                fi
}

stop() {

        PROC="$(ps -ef | grep $chk_PROC | grep -v grep | awk '{print $2}' | head -1)"
        PROC_FIM="$(ps -ef | grep $chk_PROC_FIM | grep -v grep | awk '{print $2}' | head -1)"
        if [[ -z "$PROC" && -z "$PROC_FIM" ]]; then
                                        echo "PROCESS is already stopped."
                    return
                fi

        PROC="$(ps -ef | grep $chk_PROC | grep -v grep | awk '{print $2}' | head -1)"
        PROC_FIM="$(ps -ef | grep $chk_PROC_FIM | grep -v grep | awk '{print $2}' | head -1)"
        echo "Stopping PROCESS . . ."
                if [[ "$PROC" > 0 ]]; then
               kill -9 "$PROC"
                fi
        if [[ "$PROC_FIM" > 0 ]]; then
               kill -9 "$PROC_FIM"
        fi
        sleep 1

                PROC="$(ps -ef | grep $chk_PROC | grep -v grep | awk '{print $2}' | head -1)"
        PROC_FIM="$(ps -ef | grep $chk_PROC_FIM | grep -v grep | awk '{print $2}' | head -1)"
        if [[ -z "$PROC" && -z "$PROC_FIM" ]]; then
                        echo "PROCESS stopped."
                        return
        else
                                if [[ "$chk_loop" -lt "3" ]]; then
                                        stop
                                        chk_loop=$((chk_loop+1))
                                else
                                        echo "unable to stop PROCESS"
                                        exit 1
                                fi
        fi
}

status() {
        PROC="$(ps -ef | grep $chk_PROC | grep -v grep | awk '{print $2}' | head -1)"
                PROC_FIM="$(ps -ef | grep $chk_PROC_FIM | grep -v grep | awk '{print $2}' | head -1)"
        if [ -z "$PROC" ]; then
                if [ -z "$PROC_FIM" ]; then
                                                echo "PROCESS stopped."
                                                return
                                else
                                        echo "PROCESS killed."
                                        return
                                fi
        else
                echo "PROCESS running, process $PROC. "
                                return
        fi

}

case "$1" in
        start)
                start
                ;;
        stop)
                stop
                ;;
        restart)
                stop
                start
                ;;
        status)
                status
                ;;
        *)
                echo "*** Usage: $0 {start|stop|restart|status}"
                exit 1
esac
exit 0

#########################################################

---


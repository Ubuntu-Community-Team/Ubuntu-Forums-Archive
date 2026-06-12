---
title: "Need FTP Script with Resume for automated Backups"
date: 2009-04-30
forum: Programming Talk
---

### Post by Cybie257 on 2009-04-30
Ok, so here is a run-down of what I am trying to accomplish, so any OTHER options will be appreciated beyond my current plan. 

I have a Linux Server (Ubuntu Desktop 8.10) on-site that I am sending file to an off-site Linux Server (also Desktop V8.10). 

Main Problem; Only a T1 line available at our location. :(

Needs: SSH, No files readable on remote server (Using EncFS), Scriptable.

In the beginning, I used RSync and shell scripts (automated by crontab) to send files to the server. This was working great, but the problem was, was that the files were open to whomever(prying eyes/hackers) on the remote server. I have daily backups consisting of data from different areas on a particular day.

(current) Solution: Attach to the remote server vis SSHFS, mounting the remote encrypted directory to the local machine. Then, mounting the local directory/volume to the local directory used for decrypting. In other words, I have both, the encrypted and decrypted files within the local machine, while the remote server will only show the encrypted files. Perfect situation. Except....

Problem: 
Some of the files are huge. the biggest being about 9GB from the SQL Server weekly backup. The SSHFS volume keeps dropping connection at random times, and due the the T1 speed, always manages to hit the 9GB file, requiring the next time the script is run, to begin the transfer(s) from the beginning, wasting all sorts of bandwidth.

I already know that Rsync had a resume option. But,the way it works, I might as well start the transfer over from the beginning as Rsync wants to compare byte-for-byte before continuing causing it to use the same bandwidth as a new copy. Not much of a resume feature as I see it. 

Current Solution where a new problem arises:
I am currently attempting to use FTP as the option as proftpd allows for file resume and is very quick. The problem I now encounter is this:

    "How do I write the ftp command (in a script) to get the byte marker in order to resume the transfer(s)?" 

I've tried manually using restart, but it tends to want to restart at the 0 byte offset. Using GUI apps, I have no problems getting it to resume. Unless there is a GUI app that I can program and schedule to do such backups/transfers, FTP is a problem. 


What I am looking for from the community: 

How to I start an ftp transfer to compare files and restart them at the proper byte offset. (via command line and scripts)

OR

What can someone recommend to use for off-site backups that is programmable and schedule-able. 

Thanks in Adnvance!!! 
-Cybie

EDIT: One more detail I should note. When my SSHFS volume drops, I have a script that runs every 15 minutes to check for connectivity. If it is disconnected, it automatically re-establishes connections. The script has already timed out and the file that was copying will be partial, causing the next run of the script to start the transfer of that file from the beginning. Not good when you got 80% of a 9GB file copied and it has to start all over again. :(

---


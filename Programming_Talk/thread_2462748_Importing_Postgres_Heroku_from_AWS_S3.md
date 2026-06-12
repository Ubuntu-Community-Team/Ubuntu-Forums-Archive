---
title: "Importing Postgres Heroku from AWS S3"
date: 2021-05-27
forum: Programming Talk
---

### Post by Drone4four on 2021-05-27
I&#8217;m learning how to handle Postgres instances by backing them up and restoring them on Heroku for a Django project (a small rudimentary CMS). The amount of data is a few hundred kilobytes because it's just text that I am storing in my my db. 

I downloaded the binary data to my local machine [using this particular section]("https://devcenter.heroku.com/articles/heroku-postgres-backups#downloading-your-backups") of the Heroku doc.

[The next step]("https://devcenter.heroku.com/articles/s3") was to create an AWS account, including setting up Access Keys which I located in the dashboard and entered them into my local dev environment. I named my bucket. I uploaded the binary to S3.

I&#8217;ve made it all the way to[ the end of Heroku&#8217;s import Postgres guide]("https://devcenter.heroku.com/articles/heroku-postgres-import-export").

I install  the `awscli` package with pip which [enabled me to presign my s3 bucket]("https://devcenter.heroku.com/articles/heroku-postgres-import-export#import-to-heroku-postgres") (which succeeded). 

I am right at the final step of importing my backup to Heroku Postgres. I am so close!

My traceback at this point indicates that Heroku is expecting an HTTP 200 (request has succeeded) but instead it receives an HTTP 400 (can&#8217;t process) &#8216;due to the source URL being inaccessible&#8217;. This points towards the restrictive permissions in place on my AWS S3 bucket. 

You can find my traceback in full at the bottom of this post.

With regards to my AWS S3 bucket, in the dashboard, the main Permissions switch relevant here is the &#8220;Block all public access&#8221; option. Whether this checkbox is enabled or disabled (I carefully tried both), I encountered the same HTTP 200/400 in my traceback. This is where I believe the issue is. 

I&#8217;m not sure what else to try. I&#8217;m also a little concerned that with the vast number of variables available for Amazon&#8217;s S3 service, I don&#8217;t know how I might share or export my configuration nicely for you people to take a closer look. What other information could I provide to better help you people help me?

> 
$ heroku pg:backups:restore 'https://postgres-restore-<project-name>.s3.amazonaws.com/2021May<hash redacted>aa9376\?X-Amz-Algorithm\=AWS4-HMAC-SHA256\&X-Amz-Credential\=AKIAY<hash redacted>0527%2FOhio%2Fs3%2Faws4_request\&X-Amz-Date\=2021<hash redacted>33Z\&X-Amz-Expires\=3600\&X-Amz-SignedHeaders\=host\&X-Amz-Signature\=19<hash redacted>17' HEROKU_POSTGRESQL_PUCE -a <project-name> 
 &#8250;   Warning: heroku update available from 7.50.0 to 7.51.0.
 &#9656;    WARNING: Destructive Action
 &#9656;    This command will affect the app <project-name>
 &#9656;    To proceed, type <project-name> or re-run this command with
 &#9656;    --confirm <project-name>

> <project-name>
Starting restore of https://postgres-restore-<project-name>.s3.amazonaws.com/<redacted>-802a-4409-8624-<redacted>\?X-Amz-Algorithm\=<redacted>\&X-Amz-Credential\=<redacted>%2F20210527%2FOhio%2Fs3%2Faws4_request\&X-Amz-Date\=20210527T101733Z\&X-Amz-Expires\=3600\&X-Amz-SignedHeaders\=host\&X-Amz-Signature\=199<hash redacted>d86a0317 to postgresql-animate-93816... done

Use Ctrl-C at any time to stop monitoring progress; the backup will continue restoring.
Use heroku pg:backups to check progress.
Stop a running restore with heroku pg:backups:cancel.

Restoring... !
 &#9656;    An error occurred and the backup did not finish.
 &#9656;    
 &#9656;    waiting for restore to complete
 &#9656;    pg_restore finished with errors
 &#9656;    waiting for download to complete
 &#9656;    download finished with errors
 &#9656;    please check the source URL and ensure it is publicly accessible
 &#9656;    
 &#9656;    Run heroku pg:backups:info r019 for more details.

$ heroku pg:backups:info r019 -a <project-name>
 &#8250;   Warning: heroku update available from 7.50.0 to 7.51.0.
=== Backup r019
Database:         BACKUP
Started at:       2021-05-27 10:29:02 +0000
Finished at:      2021-05-27 10:29:02 +0000
Status:           Failed
Type:             Manual
Backup Size:      0.00B (0% compression)

=== Backup Logs
2021-05-27 10:29:02 +0000 2021/05/27 10:29:02 aborting: could not write to output stream: Expected HTTP Status 200, received: "400 Bad Request"
2021-05-27 10:29:02 +0000 pg_restore: error: could not read from input file: end of file
2021-05-27 10:29:02 +0000 waiting for restore to complete
2021-05-27 10:29:02 +0000 pg_restore finished with errors
2021-05-27 10:29:02 +0000 waiting for download to complete
2021-05-27 10:29:02 +0000 download finished with errors
2021-05-27 10:29:02 +0000 please check the source URL and ensure it is publicly accessible
$


---


---
title: "SVN Server How-to"
date: 2009-11-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Thomas_SD on 2009-11-23
I set up an SVN server in Debian 4.0 but all of the instructions here should be identical in Ubuntu. I had to use a lot of sources for this and thought it would be good to have it all in one place in case anyone else wants to attempt this in the future. The SVN server here uses Apache and WebDAV so it will create a web interface to the repository as well as access from a shell. Also, there is a section where you can set the server to allow anonymous read-only access if you choose as well as a short primer on common SVN client commands from a shell.

How To Get SVN server running in Debian

All of these commands were executed as root but I don't know if that's necessary for all of them.

1. Login as root.
```
su
```

2. Download packages.
```
apt-get install apache2 libapache2-svn subversion subversion-tools
```

3. Create an SSL certificate. Answer all the questions it asks.
```
make-ssl-cert
```

4. Create a new Apache configuration. Name it whatever you want (I am using the name 'ssl' below).
```
cd /etc/apache2/sites-available
cp default ssl
```

5. Create a symlink to ssl.
```
cd /etc/apache2/sites-enabled
ln -s ssl /etc/apache2/sites-available/ssl
```

6. Modify /etc/apache2/ports.conf.
```
cd /etc/apache2
vi ports.conf
```
Add the line
```
Listen 443
```

7. Modify /etc/apache2/sites-available/ssl to use port 443 instead of port 80. My config file reads:

```
	NameVirtualHost *:443
	<VirtualHost *:443>
		LoadModule ssl_module /usr/lib/apache2/modules/mod_ssl.so
		SSLEngine On
		SSLCertificateFile /etc/apache2/ssl/apache.pem
		...
	</VirtualHost>

```

8. Restart Apache
```
/etc/init.d/apache2 restart

```

9. Check that https works in a web browser.
```
[https://hostname](https://hostname) (should display an "It works!" message)

```

10. Create a repository. I'm using /home/svn/ as the base directory and repo1 as the repository. You can change those.
```
cd /home
mkdir svn
cd svn
vi test (put something like "test" in this file and save it with `:wq' command)
su www-data
svnadmin create /home/svn/repo1
svn import /home/svn/test file:///home/svn/repo1/test -m "Test."

```

11. Restart Apache.
```
/etc/init.d/apache2 restart

```

12. Modify /etc/apache2/sites-available/ssl to add location of repository.
```
cd /etc/apache2/sites-available
vi ssl

```

At the bottom of the file (but above </VirtualHost>) add in the lines:
```

		<Location /svn/repo1>
			DAV svn
			SVNPath /home/svn/repo1
			AuthType Basic
			AuthName "Repository 1"
			AuthUserFile /home/svn/repo1/.dav_svn.passwd
			Require valid-user
		</Location>

```

12a. To enable anonymous users to have read-only access use the following instead:
```
		<Location /svn/repo1>
			DAV svn
			SVNPath /home/svn/repo1
			AuthType Basic
			AuthName "Repository 1"
			AuthUserFile /home/svn/repo1/.dav_svn.passwd
			<LimitExcept GET PROPFIND OPTIONS REPORT>
				Require valid-user
			</LimitExcept>
		</Location>

```

13. Add the first user.
```
su www-data -c "htpasswd -c -m /home/svn/repo1/.dav_svn.passwd username1"

```

14. Add additional users. Be careful not to have the -c flag inside the quotes. That would erase any previous users entered.
```
su www-data -c "htpasswd -m /home/svn/repo1/.dav_svn.passwd username2"
su www-data -c "htpasswd -m /home/svn/repo1/.dav_svn.passwd username3"

```

15. You should be able to checkout the repository now. The server is "https://hostname/svn/repo1". See below for common SVN client commands.

16. Additional repositories are created using steps 10 - 14.


Common SVN Commands 
Get latest code:
```
svn up 

```

See the log file:
```
svn log | less

```
The | means pipe the output of svn log to less. less just prints the output to the terminal. Combining the two commands will print the output of svn log to a terminal.

Check the status of the local files:
```
svn st

```
This shows which files have been modified locally.

Commit changes:
```
svn ci -m “Message goes here.” 

```
When using just a short message to describe changes.
```
svn ci -F logmsg

```
Where logmsg is a text file describing the changes made.

To see the differences between local code and checked in code:
```
svn diff | less 

```

To check out the latest code:
```
svn co [http://hostname/svn/repo1](http://hostname/svn/repo1)

```

To check out a specific directory only:
```
svn co [http://hostname/svn/repo1/subdir](http://hostname/svn/repo1/subdir)

```

Check out an older revision of a specific directory:
For example, to get revision 51 of subdir/ directory
```
svn co -r 51 [https://hostname/svn/repo1/subdir](https://hostname/svn/repo1/subdir)
```


To set ignore property on a directory for a specific filename extension:
```
svn pedit svn:ignore .
```
That will open up a text editor like vi with a file. Then to ignore all *.jpg files put in that file:
```
*.jpg
```
Save it (it's okay to just use the default filename) and exit.

To set ignore property on a directory for a specific file:
```
svn pedit svn:ignore .
```
That will open up a text editor like vi with a file. Then to ignore the specific file x.pdf file put in that file:
```
x.pdf
```
Save it (it's okay to just use the default filename) and exit. The ignore property allows you to have files in a directory but SVN knows that you don't want to commit them. This is especially useful when you have lots of large images in a directory and you don't want to take up server space or have to download those files every time you check out the repository.

---


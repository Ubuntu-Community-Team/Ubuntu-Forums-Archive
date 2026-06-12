---
title: "[Python] FTP script is hanging"
date: 2012-01-02
forum: Programming Talk
---

### Post by Sworddragon on 2012-01-02
I have written a script in Python which connects to a FTP server and uploads some data. I'm using it for daily automatic backups. The problem is if my internet connection gets lost and connected again my script will hang. In my case my provider disconnects me after 24 hours and gives me a new ip address. Here is the script:

```
#!/usr/bin/python -OOtt
# coding=utf-8
import StringIO, argparse, ftplib, os, socket, sys, time

class backup:
	def __init__(self):
		arguments = argparse.ArgumentParser()
		arguments.add_argument('--serverdir', default = '.', dest = 'serverdir', help = 'The directory on the server where the backup is stored')
		arguments.add_argument('-d', '--device', default = 'sr0', dest = 'device', help = 'Selects the device which data is backuped')
		arguments.add_argument('-l', '--limit', type = int, dest = 'limit', help = 'Selects the upload limit in bytes')
		arguments.add_argument('-p', '--password', required = True, dest = 'password', help = 'The password for the ftp server')
		arguments.add_argument('-s', '--server', required = True, dest = 'server', help = 'The address of the ftp server')
		arguments.add_argument('-u', '--user', required = True, dest = 'user', help = 'The username for the ftp server')
		option = arguments.parse_args()
		if option.limit != None and option.limit <= 0:
			print('The upload limit must be 1 or higher')
			exit()
		if option.serverdir == '':
			print('The server directory is invalid')
			exit()
		mount = True
		if os.system('sudo mount \'/dev/' + option.device + '\' \'/media/' + option.device + '\' -o ro -t iso9660 > /dev/null 2>&1') == 0:
			mount = False
		while 1:
			try:
				self.connection = ftplib.FTP(option.server, option.user, option.password)
				break
			except socket.error:
				time.sleep(1)
		serverdir = option.serverdir
		if serverdir[-1] == '/':
			serverdir = serverdir[:-1]
		i = 1
		while self.file_exists(serverdir + '_old-' + str(i)) == True:
			i += 1
		if self.file_exists(serverdir) == True:
			self.connection.rename(serverdir, serverdir + '_old-' + str(i))
			while self.file_exists(serverdir + '_old-' + str(i)) == False:
				time.sleep(1)
		self.makedirs(serverdir)
		for object in os.listdir('/media/' + option.device):
			file = open('/media/' + option.device + '/' + object)
			if option.limit != None:
				self.connection.storbinary('STOR ' + serverdir + '/' + object, file, option.limit, self.control)
			else:
				self.connection.storbinary('STOR ' + serverdir + '/' + object, file)
			file.close()
		if self.file_exists(serverdir + '_old-' + str(i)) == True:
			self.rmdir(serverdir + '_old-' + str(i))
		self.connection.quit()
		if mount == False:
			os.system('sudo umount \'/dev/' + option.device + '\'')

	def control(self, chunk):
		time.sleep(1)

	def file_exists(self, path):
		directory = path.split('/')
		last_directory = ''
		for object_1 in directory:
			if object_1 == '':
				continue
			for object_2 in self.get_files(last_directory):
				if object_1 == object_2:
					last_directory += object_1 + '/'
					break
			if object_1 != object_2:
				return False
		return True

	def get_files(self, path):
		stdout = StringIO.StringIO()
		sys.stdout = stdout
		self.connection.dir(path)
		list = stdout.getvalue()[:-1]
		stdout.close()
		sys.stdout = sys.__stdout__
		file = []
		for entry in list.split('\n'):
			file.append(entry.split()[-1])
		return file

	def makedirs(self, path):
		directory = path.split('/')
		last_directory = ''
		for object in directory:
			if object == '':
				continue
			if self.file_exists(last_directory + object) == False:
				self.connection.mkd(last_directory + object)
				last_directory += object + '/'

	def rmdir(self, path):
		for object in self.connection.nlst(path):
			if object == '.' or object == '..':
				continue
			try:
				self.connection.size(path + '/' + object)
				self.connection.delete(path + '/' + object)
			except:
				self.rmdir(path + '/' + object)
		self.connection.rmd(path)

backup()
```

It seems self.connection.storbinary is causing the problem. It doesn't send any data or is raising an exception. I could use threads and check if the transfer is aborted. But with this way I must resend the complete data every time if the connection gets lost. Maybe somebody know how I could continue the transfer if the connection gets lost.

---

### Post by Sworddragon on 2012-01-10
I have opened a ticket at the Python bugtracker for this: [http://bugs.python.org/issue13714](http://bugs.python.org/issue13714)

This problem appears if the ip address changes during a connection. But Python can't do anything to detect the change and correcting the ftp connection.

I have now found another solution. I'm using the timeout argument and counting how many data I have send. After a disconnect I'm opening a new connection and sending the rest of the data (this is looped because I have to wait until the first connection got a timeout from the server because it blocks the file).

---


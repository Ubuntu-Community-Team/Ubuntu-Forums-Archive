---
title: "web proxy in python"
date: 2011-03-06
forum: Programming Talk
---

### Post by pishman on 2011-03-06
hi, i'm not sure if I write into the appropriate forum, but anyway, those who feel its inappropriate, ignore the post please.
here is a proxy (http and https) written in python.  Though the code made need some polishing, itt works and since I used a lot of help from these and other forums when writing it.

cheers

!/usr/bin/python
from urlparse import urlparse
from threading import Thread
import string
import sys
import select
import socket
import string
import threading
import thread
import urllib
import ssl
import time
import os

os.system('clear')

class simon_server():
    def __init__ (self, server_host, server_port):
        self.server_host = server_host
        self.server_port = server_port
    self.server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    self.server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, -1)
        here = (self.server_host, self.server_port)
        self.server_socket.bind (here)
        self.server_socket.listen (5)
        print 'simon is up at: ' + str(here)
        while 1:
            (self.conn, self.addr) = self.server_socket.accept()
            try:
        start_thread = thread.start_new_thread(simon_thread, (self.conn, self.addr))
            except Exception, errtxt:
                print errtxt
        break
        sys.exit(1)
            finally:
                next

class simon_thread():
    def __init__(self, conn, addr):
        self.conn = conn
        self.addr = addr
        print 'a thread is up at ' + str(self.addr)
        self.client_request = self.conn.recv(8192)
        parse_list = self.parse_request()
        html_request = parse_list[0]
    print 'clinet requested ' + str(html_request)
        scheme = parse_list[1]
    #print scheme + '\n'
        host = parse_list[7]
        netloc = parse_list[2]
    path = parse_list[3]

############ ignore https for the moment        
        if scheme == 'https':
        print 'INTO THE HTTPS LOOP'

## ESTABLISH SECURE CONNECTION AT 443
        self.to_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        print 'CLIENT REQUESTED SECURE CONNECTION TO ' + str(path)
        try:
        self.to_server_socket.connect((host, 443))
        except:
                exception = sys.exc_info()[1]
                print 'CONNECTION ATTEPT TO ' + str(path) + ' FAILED BECAUSE:' + str(exception)
        sys.exit(1)
        finally:
        print 'SECURE CONNECTION TO REMOTE HOST ' + str(path) + ' ESTABLISHED'

## NOTIFY CLIENT THAT CONNECTION IS ESTABLISHED
        buffer = 'HTTP/1.1 200 OK \r\n\r\n'
            self.conn.send(buffer)
        buffer = '\r\n\r\n'
        self.conn.send(buffer)
        print 'CLIENT CONNECTED TO ' + str(path)

## ENTER COMMUNICATIONS LOOP
        print 'ENTER SECURE COMMUNICATION LOOP WITH ' + str(path)

        self.conn.setblocking(0)
        self.to_server_socket.setblocking(0)

        while 1:
        try:

            print 'SIMON IS LISTENING'
            buffer_client = ''
            buffer_remote = ''

                    rlist, wlist, elist = select.select([self.conn], [], [], 0.01)
                    if rlist:
                buffer_client = self.conn.recv(8192)

                    rlist, wlist, elist = select.select([self.to_server_socket], [], [], 0.01)
                    if rlist:
                buffer_remote = self.to_server_socket.recv(8192)

            if (buffer_client != ''):
                print 'THE CLIENT PASSED INFO'
                while 1:                
                            rlist, wlist, elist = select.select([], [self.to_server_socket], [], 0.01)    
                            if wlist:
                                self.to_server_socket.send(buffer_client)
                        print 'SENDING DATA TO REMOTE'
                                break
                            else:
                        pass
            else:
                pass


            if (buffer_remote != ''):
                print 'THE REMOTE PASSED INFO'
                while 1:
                            rlist, wlist, elist = select.select([], [self.conn], [], 0.01)
                            if wlist:
                                self.conn.send(buffer_remote)
                        print 'SENDING DATA TO LOCAL'
                                break
                            else:
                                pass

        except:
                    exception = sys.exc_info()[1]
                    print 'CONNECTION TO ' + str(path) + ' FAILED BECAUSE:' + str(exception)
            print 'THREAD IS DOWN'
            sys.exit(1)
        finally:
            pass


        print buffer_client    
        buffer_client = ''

                                
############ else means that the sceme is http
        else:
        print 'into the http loop'
        print 'client requested non-sequre connection to ' + str(netloc)
            self.to_server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            self.to_server_socket.connect((host, 80))
            self.to_server_socket.setblocking(0)

############# wait until the socket is writable
            while 1:
                rlist, wlist, elist = select.select([], [self.to_server_socket], [])    
                if wlist:
                    self.to_server_socket.send(self.client_request)
            print 'sending data to ' + str(netloc)
                    break
                else:
                    pass

############# wait until the socket is readable
            while 1:
                rlist, wlist, elist = select.select([self.to_server_socket], [], [], 3)
                if rlist:
                    buffer = self.to_server_socket.recv(8192)
                    if buffer != '':
                        self.conn.send(buffer)
            print 'receiving data from ' + str(netloc)
                    else:
                        print 'connection to ' + str(netloc) + 'closed because no buffer'
                        self.to_server_socket.close()
                        break

############## check for timeout    
                if [rlist, wlist, elist] == [[], [], []]:
                    print 'connection to ' + str(netloc) + ' closed because of timeout'
                    self.to_server_socket.close()
                    break
        
        self.conn.close()
        print 'thread is closed'
        print '\n'
        print '\n'

#################################
    def parse_request (self):
        parse_list = []
        position = self.client_request.find('\n')
        html_request = self.client_request[0:position]
        html_request = html_request[0:len(html_request)]
        parse_list.append(html_request)
        check = html_request.find('CONNECT')
        if (check != -1):
            html_request = html_request.replace(':443', '')
            html_request = html_request.replace('CONNECT', '')
            html_request = html_request.replace('http://', '')
            html_request = html_request.replace('POST ', '')
            html_request = html_request.replace('GET ', '')
            html_request = html_request.replace('HTTP/1.1', '')
            html_request = html_request.replace('HTTP/1.0', '')
            html_request = html_request.replace('\n','')
            html_request = html_request.replace('\r','')
            scheme, netloc, path, params, query, fragment = urlparse(html_request)
            path = path.replace(' ', '')
            check = path.find('/')
            if check != -1:
                path = path[0:check]
            else:
                pass
        try:
                host = socket.gethostbyname(path)
        except:
            'AN ATTEMPT TO ID ' + str(path) + ' FAILED'
        finally:
            pass
            scheme = 'https'
        else:
            html_request = html_request.replace('POST ', '')
            html_request = html_request.replace('GET ', '')
            html_request = html_request.replace('HTTP/1.1', '')
            html_request = html_request.replace('HTTP/1.0', '')
            html_request = html_request.replace('\n','')
            html_request = html_request.replace('\r','')
            scheme, netloc, path, params, query, fragment = urlparse(html_request)
        try:
                host = socket.gethostbyname(netloc)
        except:
            'AN ATTEMPT TO ID ' + str(netloc) + ' FAILED'
        finally:
            pass
        parse_list.append(scheme)
        parse_list.append(netloc)
        parse_list.append(path)
        parse_list.append(params)
        parse_list.append(query)
        parse_list.append(fragment)
        parse_list.append(host)

        return parse_list




server = simon_server('XXX.XXX.XXX.XXX', 8060)

---

### Post by gmargo on 2011-03-06
I'd be pleased to take a look at this code.  But it is impossible since, as you know, python is dependent on indentation.

Please repost your code using "[ CODE ]" ... "[ /CODE ]" tags (without spaces) to preserve the indentation.

---

### Post by juancarlospaco on 2011-03-06
Use code tags, its interesting, but a waste if you cant read it.

---


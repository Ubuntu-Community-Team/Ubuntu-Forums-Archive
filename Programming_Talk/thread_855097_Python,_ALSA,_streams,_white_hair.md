---
title: "Python, ALSA, streams, white hair"
date: 2008-07-10
forum: Programming Talk
---

### Post by archivator on 2008-07-10
It's been a long time since I last posted here.

My newest project is giving me serious trouble. Basically, the application is supposed to receive streaming audio from a socket and play it. In the meantime, it should capture audio and send it through that same socket. 

I seem to be lacking the foundations here.

First off, the audio is 8 kHz, 16-bit. That makes it 16KB/sec but at any given time I'm getting around 15.7-15.9 KB/sec from the socket. Naturally, this means that there would be a latency. Only problem is, I've got no idea how to buffer the audio. My approach (see below) is no better than the alternative - i.e., just dump the data from the socket to the playback thread.

Also, pyalsaaudio is a mess. There, I said it. I would gladly dump it in favor of another library but nothing else has nonblocking writes and reads (I'm looking at you, PortAudio!). The period size that the manual talks so much about has absolutely no effect in non-blocking mode and I have no idea what value I should give it. 

Here's what I have at the moment. The queues are deque objects used for communication between the main thread and the playback and capture ones. Mind you, I'm not using the capture thread at the moment as I'd like to get playback working first. 

```
    count = 0
    send_buff = r''
    buff = r''
    while 1:
        read, write, emptyy = select.select([client], 
                                            [],
                                            [])
        for socket in read:           
            buff = ''.join((buff,socket.recv(48))) # data always comes in 48 B packets; also, this is claimed to be faster than buff += socket.recv(48)
            count += 1
            if count % 15 == 0:
                if len(send_buff) > 0:
                    playback_queue.append(send_buff)
                send_buff = '%s' % buff # the send buffer is always 15 packets behind buff 
                buff = r''

        for socket in write:
            # not select'd
            while len(capture_queue) == 0:
                    sleep(0.00001)
            socket.send(capture_queue.pop())

```

The playback thread is also obvious:

```

class PlaybackThread(Thread):
    def __init__(self, queue):
        Thread.__init__(self, name="PlaybackThread")
        self.queue = queue
        
        self.stream = alsa.PCM(alsa.PCM_PLAYBACK, alsa.PCM_NONBLOCK)
        self.stream.setrate(8000)
        self.stream.setchannels(1)
        self.stream.setformat(alsa.PCM_FORMAT_S16_LE)
        self.stream.setperiodsize(24) # == 48 bytes
    
    def run(self):
        stream = self.stream # premature optimization FTW!
        queue = self.queue # premature optimization FTW!

        while True:
            while len(queue) == 0: # the thread starts before receiving data
                sleep(0.0000001)
            
            buff = queue.pop()
            if stream.write(buff) == 0:
                print "overrun, %i b not written" % len(buff)

```

This might seem like an obvious question to some of you but I haven't done any audio programming before (other than a few PortAudio apps but that's too easy). I guess what I'm asking is, how do I get rid of the constant pops I'm hearing (which I assume are sings of buffer underruns)? What am I doing wrong?

Thanks for your time. :)

---

### Post by ssavelan on 2008-11-03
I wish I knew.  I am just starting to look at audio and python and have been hard-pressed to find a quick solution.  Python, for being my favorite language is a weak on sound.  I wonder if people often roll their own but, where to start?

I have been looking at pygame a bit to try to join in with something popular and documented.  Just thought that I would post as I have been having a similar time of it.

Thanks for posting the code though...

---

### Post by Paul Miller on 2008-11-05
I'd say forget about ALSA and look at PyGame instead.

---

### Post by Endolith on 2009-09-09
Pygame can do streaming audio input?

[http://stackoverflow.com/questions/742546/get-the-amplitude-at-a-given-time-within-a-sound-file](http://stackoverflow.com/questions/742546/get-the-amplitude-at-a-given-time-within-a-sound-file)

[http://stackoverflow.com/questions/519851/good-sound-processing-analysis-capturing-modules](http://stackoverflow.com/questions/519851/good-sound-processing-analysis-capturing-modules)

[This guy]("http://medi.uni-oldenburg.de/members/jnix/index.html#thesisdownload") wrote a module for ALSA, but I don't know if he published it.

---


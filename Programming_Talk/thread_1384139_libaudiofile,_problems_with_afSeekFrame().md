---
title: "libaudiofile, problems with afSeekFrame()"
date: 2010-01-18
forum: Programming Talk
---

### Post by skullmunky on 2010-01-18
I have some audio code which has worked well for many years and now suddenly doesn't anymore, since upgrading to ubuntu 9.04.  It uses libaudiofile.  It suddenly has problems with looping sounds and with playing sounds more than once; both of these seem to be related to the function afSeekFrame().

For example, the looping code looks like this:

```

// Reads the samples out of a AIFF audio file into tempbuffer_ 
int SampleFile::readAFFrames(void)
	{
	int numRead = afReadFrames(afFile_, AF_DEFAULT_TRACK, tempBuf_, inputFrames_);
	if (numRead < 0)
		{
		perror(filename_);
		stop();
		return 0;
		}
	if (numRead < inputFrames_)
		{
		if (loop_)
			{
			while (numRead < inputFrames_)
				{
				afSeekFrame(afFile_, AF_DEFAULT_TRACK, 0);
				int n = afReadFrames(afFile_, AF_DEFAULT_TRACK,
						tempBuf_ + numRead*frameSize_,
						inputFrames_ - numRead);
				if (n <= 0)
					{
					perror(filename_);
					stop();
					return 0;
					}
				numRead += n;
				}
			}
		else
			{
			memset(tempBuf_ + numRead*frameSize_, 0, (inputFrames_ - numRead)*frameSize_);
			stop();
			}
		}
	convertFrames();
	return 1;
	}

```

it's supposed to know that it's reached the end of the file when afReadFrames() returns less than the number of frames requested.  If the looping flag is turned on, it's supposed to go back to the beginning by calling afSeekFrame(afFile_,AF_DEFAULT_TRACK,0).  But, it doesn't seem to do that - it just sits and stutters on the last frame of the file.  

did something happen to libaudiofile?  has something changed recently?  do I have to scrap this and use libsndfile instead?

---


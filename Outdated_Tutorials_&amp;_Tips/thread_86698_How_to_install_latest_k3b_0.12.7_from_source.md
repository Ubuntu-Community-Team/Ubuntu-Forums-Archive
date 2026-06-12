---
title: "How to install latest k3b 0.12.7 from source"
date: 2005-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2005-11-06
Hi,
    I have had difficulties in erasing and rewriting on a DVD-RW that was formated in windows and found that the newer k3b version 0.12.7 has some fixes, but could not find a working deb. I thus had to build from source and here is the process:

_Howto update K3B to 0.12.7 in Breezy kubuntu_

If you are having problems with erasing and writing to a DVD-RW that was formatted on windows before, you may need to update from version 0.12.2 to the latest 0.12.7. A deb file is not yet available in the repositories and I built from source very successfully, but quite a few dependancies need to be installed, so have your repositories enabled.
Download the latest version from [http://mesh.dl.sourceforge.net/sourceforge/k3b/k3b-0.12.7.tar.bz2](http://mesh.dl.sourceforge.net/sourceforge/k3b/k3b-0.12.7.tar.bz2) 
Put the file on your desktop and right click and extract to here. Rename the extracted folder with a simpler name i.e. K3b.
Now go to the K3b website and follow their installation guide give below. Use synaptic to install the dependancies, which are mostly the dev files. Use search in synaptic in name and description to find them. Run ./configure everytime and check the last part of the results for “no” and find those  dependancies in synaptic, install and rerun ./configure until you are happy. They are all there in the repos. Once you have all repos, then you can make and install. I suggest uninstalling the older version with Synaptic before doing the new install.
Here we go:

The first thing to do is to get the requirements installed (see requirements below). You need to at least install the Qt and kdelibs devel packages.
For a working audio player you need the kdemultimedia devel package.
For mp3 decoding support you need to install libmad.
For FLAC decoding and encoding support you need to install the FLAC++ libraries and headers.
For Ogg Vorbis decoding and encoding you need to install the Ogg Vorbis libraries and headers.
Get the source from the K3b download page (Example: k3b-0.11.10.tar.bz2)
Put the source file on your desktop, right click and select extract here. A folder with the source files will be created on your desktop. Rename the folder to a simpler name such as k3b 
and cd in to this folder 
# cd /home/<username>/Desktop/k3b
Configure the source: 
# ./configure
After the configuration finished you will see a summary. If one of the features you want to be enabled is not you need to check the requirements again and install after searching with Synaptic. See requirements below.
Start the compilation once you are happy: 
# make
And finally if the command above did not show any errors install K3b: 
# sudo make install
Now you may start K3b from the KMenu (Multimedia section). If you had the older version installed the icons should be right immediately from start. 

K3b 0.12 Requirements (Dependancies)
KDE already installed in Breezy. 
QT >= 3.2 KDE 3.2 requires the QT library version 3.2, a cross-platform GUI development toolkit. Since K3b is a threaded application QT needs to be compiled with threading support enabled. 
cdrecord/mkisofs - Cdrecord creates home-burned CDs with a CD-R/CD-RW recorder. 
dvd+rw-tools - The DVD+RW-Tools are used to burn and format DVD+R(W) and DVD-R(W) media. For DVD+R Double Layer burning version >= 5.20.4.10.8 is required. 

Optionally: 
cdrdao - Cdrdao records audio or data CD-Rs in disk-at-once (DAO) mode based on a textual description of the CD contents (toc-file). 
MAD MPEG Audio Decoder Library - MAD is a high-quality MPEG audio decoder. It currently supports MPEG-1 and the MPEG-2 extension to lower sampling frequencies, as well as the de facto MPEG 2.5 format. All three audio layers - Layer I, Layer II, and Layer III (i.e. MP3) - are fully implemented.
Used by the Mp3 decoding plugin. 
cdparanoia devel - Cdparanoia is a Compact Disc Digital Audio (CDDA) extraction tool, commonly known on the net as a 'ripper'. 
transcode - transcode is a linux text-console utility for video stream processing. 
Ogg Vorbis library - Ogg Vorbis is a completely open, patent-free, professional audio encoding and streaming technology with all the benefits of Open Source.
Used by the Ogg Vorbis decoding and encoding plugins. 
FLAC++ library - FLAC stands for Free Lossless Audio Codec. Grossly oversimplified, FLAC is similar to MP3, but lossless, meaning that audio is compressed in FLAC without any loss in quality. This is similar to how Zip works, except with FLAC you will get much better compression because it is designed specifically for audio, and you can play back compressed FLAC files in your favorite player (or your car or home stereo, see links to the right for supported devices) just like you would an MP3 file.
Used by the FLAC decoding plugin. 
VCDImager - A full-featured mastering suite for authoring, disassembling and analyzing Video CD's and Super Video CD's. 
Normalize - normalize is a tool for adjusting the volume of audio files to a standard level. This is useful for things like creating mixed CD's and mp3 collections, where different recording levels on different albums can cause the volume to vary greatly from song to song. 
eMovix - eMoviX is a tiny Linux CD distribution containing all the software to boot from a CD and play automatically every video file localized in the CD root. 
SoX - SoX is the swiss army knife of sound processing programs. SoX is a command line utility that can convert various formats of computer audio files in to other formats.
Used by the SoX audio encoding plugin. 
Lame - LAME is an LGPL MP3 encoder. The Open source development model allowed to improve its quality and speed since 1999. It is now an highly evolved MP3 encoder, with quality and speed able to rival state of the art commercial encoders.
Used by the external audio encoding plugin. 
Musepack (libmpcdec) - Musepack is an audio compression format with a strong emphasis on high quality. It's not lossless, but it is designed for transparency, so that you won't be able to hear differences between the original wave file and the much smaller MPC file.
Used by the Musepack audio decoding plugin. 
libsndfile - Libsndfile is a C library for reading and writing files containing sampled sound (such as MS Windows WAV and the Apple/SGI AIFF format) through one standard library interface.
Used by the libsndfile audio decoding plugin. 
ffmpeg - FFmpeg is a complete solution to record, convert and stream audio and video. It includes libavcodec, the leading audio/video codec library. FFmpeg is developed under Linux, but it can compiled under most operating systems, including Windows.
Use by the ffmpeg audio decoding plugin. 
Musicbrainz (libmusicbrainz) - The MusicBrainz client library (also referred to as mb_client and libmusicbrainz) is a development library geared towards developers who wish to add MusicBrainz lookup capabilities to their applications.
MusicBrainz is a user-maintained community music metadatabase. Music metadata is information such as the ArtistName, the AlbumTitle, and the list of tracks that appear on an album.
Use by K3b to automatically fill in CD-Text information in an audio CD project. 
HAL - HAL is a piece of software that provides a view of the various hardware attached to a system. In addition to this, HAL keeps detailed metadata for each piece of hardware and provide hooks such that system- and desktop-level software can react to changes in the hardware configuration in order to maintain system policy.
Using HAL K3b is able to add and remove devices while running (for example usb or firewire devices that are turned on while K3b is running).

---

### Post by rcjhawk on 2006-07-30
> **Matchless said:**
> 
Start the compilation once you are happy: 
# make
And finally if the command above did not show any errors install K3b: 
# sudo make install


Couple of things:

1) By default, most configure files will put the executable at /usr/local/bin/k3b rather than /usr/bin/k3b, so make sure that /usr/local/bin is in your path, as it is by default in most systems.  You could override this by doing

./configure --prefix=/usr

but I wouldn't recommend this because these files will be written over if you install a new k3b package.

2) I personally find it's better to do:

% make
% sudo checkinstall -D

which creates and installs the program as a Debian package.  In this case it's named something like k3b-0.12.7-1 .  If in the future you want to remove this package, a simple

% sudo dpkg -r k3b-0.12.7-1

will do the trick.

checkinstall is available in Universe.

---


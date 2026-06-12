---
title: "Setting up use with PVR150"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by jasontu on 2008-08-21
I recently installed Mythbuntu to be used with my Hauppauge PVR150.  I know the system detects the card and the various inputs from it, because the options to select one of them appear at various stages of the easy 302,812 step process of setting up Mythbuntu.

I thought I had everything straight, but when I hit Watch TV the screen just flickers a moment and puts me right back at the original menu.  I have no clue where to go from here.

There are waaaaaaaaaaaaaay too many options and steps to this thing, and I don't know where I messed things up.  If anyone has some suggestions or knows a good guide website, please advise.

Thank you

---

### Post by NT4usB on 2008-08-21
Run mythfrontend from a terminal:```
mythfrontend -v all
``` and look at the errors.
Usually, it's either the directory to hold recordings doesn't exist or, if it does, myth doesn't have permissions to write to it.
And yes, Live TV writes to the recording directory... so it's not really 'live' but cached so you can pause, ffw, & rewind.

---

### Post by jasontu on 2008-08-22
Wow that spewed a lot of stuff, but maybe somebody can help me with it.  I have no clue what I'm looking for here:

```
WHERE context = 'Teletext Menu' AND action = 'PREVSUBPAGE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.032 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'TOGGLETT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.032 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENURED' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.033 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUGREEN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.033 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUYELLOW' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.034 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUBLUE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.034 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUWHITE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.035 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'TOGGLEBACKGROUND' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.036 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'REVEAL' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.036 Registering Internal as a media playback plugin.
2008-08-22 07:24:18.036 MSqlQuery: DELETE FROM inuseprograms WHERE hostname = 'timmyth' and recusage = 'player' ;
2008-08-22 07:24:18.061 Disabling Settings Cache.
2008-08-22 07:24:18.061 Clearing Settings Cache.
2008-08-22 07:24:18.062 MSqlQuery: SELECT data FROM settings WHERE value = 'ArchiveDBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.063 MSqlQuery: SELECT data FROM settings WHERE value = 'ArchiveDBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.063 Disabling Settings Cache.
2008-08-22 07:24:18.063 Clearing Settings Cache.
2008-08-22 07:24:18.066 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveTempDir' AND hostname = 'timmyth'
2008-08-22 07:24:18.067 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveShareDir' AND hostname = 'timmyth'
2008-08-22 07:24:18.068 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveVideoFormat' AND hostname = 'timmyth'
2008-08-22 07:24:18.069 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveFileFilter' AND hostname = 'timmyth'
2008-08-22 07:24:18.070 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveDVDLocation' AND hostname = 'timmyth'
2008-08-22 07:24:18.070 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveDriveSpeed' AND hostname = 'timmyth'
2008-08-22 07:24:18.071 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveDVDPlayerCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.072 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveEncodeToAc3' AND hostname = 'timmyth'
2008-08-22 07:24:18.073 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveCopyRemoteFiles' AND hostname = 'timmyth'
2008-08-22 07:24:18.074 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveAlwaysUseMythTranscode' AND hostname = 'timmyth'
2008-08-22 07:24:18.075 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveUseProjectX' AND hostname = 'timmyth'
2008-08-22 07:24:18.076 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveAddSubtitles' AND hostname = 'timmyth'
2008-08-22 07:24:18.076 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveUseFIFO' AND hostname = 'timmyth'
2008-08-22 07:24:18.077 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveDefaultEncProfile' AND hostname = 'timmyth'
2008-08-22 07:24:18.078 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveMainMenuAR' AND hostname = 'timmyth'
2008-08-22 07:24:18.079 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveChapterMenuAR' AND hostname = 'timmyth'
2008-08-22 07:24:18.080 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveDateFormat' AND hostname = 'timmyth'
2008-08-22 07:24:18.081 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveTimeFormat' AND hostname = 'timmyth'
2008-08-22 07:24:18.081 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveFfmpegCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.082 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveMplexCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.083 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveDvdauthorCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.084 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveSpumuxCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.085 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveMpeg2encCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.086 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveMkisofsCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.087 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveGrowisofsCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.088 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveTcrequantCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.088 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveJpeg2yuvCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.089 MSqlQuery: SELECT data FROM settings WHERE value = 'MythArchiveProjectXCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.090 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Archive' AND action = 'TOGGLECUT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.116 Disabling Settings Cache.
2008-08-22 07:24:18.116 Clearing Settings Cache.
2008-08-22 07:24:18.117 MSqlQuery: SELECT data FROM settings WHERE value = 'FlixDBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.117 MSqlQuery: SELECT data FROM settings WHERE value = 'FlixDBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.117 Enabling Settings Cache.
2008-08-22 07:24:18.118 Clearing Settings Cache.
2008-08-22 07:24:18.118 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Netflix Browser' and hostname = 'timmyth' ;
2008-08-22 07:24:18.118 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Netflix Queue' and hostname = 'timmyth' ;
2008-08-22 07:24:18.119 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Netflix History' and hostname = 'timmyth' ;
2008-08-22 07:24:18.119 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'NetFlix' AND action = 'MOVETOTOP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.120 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'NetFlix' AND action = 'REMOVE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.124 Disabling Settings Cache.
2008-08-22 07:24:18.124 Clearing Settings Cache.
2008-08-22 07:24:18.125 MSqlQuery: SELECT data FROM settings WHERE value = 'GalleryDBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.126 MSqlQuery: SELECT data FROM settings WHERE value = 'GalleryDBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.126 Enabling Settings Cache.
2008-08-22 07:24:18.126 Clearing Settings Cache.
2008-08-22 07:24:18.128 MSqlQuery: SELECT data FROM settings WHERE value = 'GalleryDir' AND hostname = 'timmyth'
2008-08-22 07:24:18.129 MSqlQuery: SELECT data FROM settings WHERE value = 'GalleryThumbnailLocation' AND hostname = 'timmyth'
2008-08-22 07:24:18.130 MSqlQuery: SELECT data FROM settings WHERE value = 'GallerySortOrder' AND hostname = 'timmyth'
2008-08-22 07:24:18.131 MSqlQuery: SELECT data FROM settings WHERE value = 'GalleryImportDirs' AND hostname = 'timmyth'
2008-08-22 07:24:18.131 MSqlQuery: SELECT data FROM settings WHERE value = 'GalleryMoviePlayerCmd' AND hostname = 'timmyth'
2008-08-22 07:24:18.132 MSqlQuery: SELECT data FROM settings WHERE value = 'SlideshowUseOpenGL' AND hostname = 'timmyth'
2008-08-22 07:24:18.133 MSqlQuery: SELECT data FROM settings WHERE value = 'SlideshowDelay' AND hostname = 'timmyth'
2008-08-22 07:24:18.134 MSqlQuery: SELECT data FROM settings WHERE value = 'GalleryRecursiveSlideshow' AND hostname = 'timmyth'
2008-08-22 07:24:18.135 MSqlQuery: SELECT data FROM settings WHERE value = 'SlideshowOpenGLTransition' AND hostname = 'timmyth'
2008-08-22 07:24:18.135 MSqlQuery: SELECT data FROM settings WHERE value = 'SlideshowOpenGLTransitionLength' AND hostname = 'timmyth'
2008-08-22 07:24:18.136 MSqlQuery: SELECT data FROM settings WHERE value = 'GalleryOverlayCaption' AND hostname = 'timmyth'
2008-08-22 07:24:18.137 MSqlQuery: SELECT data FROM settings WHERE value = 'SlideshowTransition' AND hostname = 'timmyth'
2008-08-22 07:24:18.138 MSqlQuery: SELECT data FROM settings WHERE value = 'SlideshowBackground' AND hostname = 'timmyth'
2008-08-22 07:24:18.139 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'MythGallery' and hostname = 'timmyth' ;
2008-08-22 07:24:18.139 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'PLAY' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.140 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'HOME' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.140 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'END' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.141 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'MENU' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.141 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SLIDESHOW' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.195 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'RANDOMSHOW' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.196 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'ROTRIGHT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.197 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'ROTLEFT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.197 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'ZOOMOUT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.198 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'ZOOMIN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.198 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SCROLLUP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.199 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SCROLLLEFT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.199 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SCROLLRIGHT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.200 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'SCROLLDOWN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.200 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'RECENTER' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.201 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'FULLSIZE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.202 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'UPLEFT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.202 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'LOWRIGHT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.203 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'INFO' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.203 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'DELETE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.204 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'MARK' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.205 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Gallery' AND action = 'FULLSCREEN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.205 Registering MythGallery Media Handler 1/2 as a media handler for MEDIATYPE_DATA
2008-08-22 07:24:18.210 MSqlQuery: SELECT data FROM settings WHERE value = 'MonitorDrives' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.211 MSqlQuery: SELECT data FROM settings WHERE value = 'MediaChangeEvents' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.212 MSqlQuery: SELECT data FROM settings WHERE value = 'IgnoreDevices' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.212 Creating inactive MediaMonitor and static device list
2008-08-22 07:24:18.212 IgnoreDevices=
2008-08-22 07:24:18.219 MediaMonitorUnix::AddDevice() - Added /dev/scd0
2008-08-22 07:24:18.220 MythCDROMLinux::testMedia - Failed to get drive status of /dev/fd0
			eno: Invalid argument (22)
2008-08-22 07:24:18.225 MediaMonitorUnix::GetCDROMBlockDevices() returning sr0
2008-08-22 07:24:18.231 MediaMonitorUnix::AddDevice() - not adding /dev/scd0
                        because it appears to be a duplicate of /dev/scd0
2008-08-22 07:24:18.231 Initial device list...
/dev/scd0 (TSSTcorp CDDVDW SH-S203B  )
2008-08-22 07:24:18.231 Registering MythGallery Media Handler 2/2 as a media handler for MEDIATYPE_MGALLERY, ext(gif,jpg,png)
2008-08-22 07:24:18.232 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-08-22 07:24:18.236 Disabling Settings Cache.
2008-08-22 07:24:18.236 Clearing Settings Cache.
2008-08-22 07:24:18.237 MSqlQuery: SELECT data FROM settings WHERE value = 'GameDBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.237 MSqlQuery: SELECT data FROM settings WHERE value = 'GameDBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.238 Enabling Settings Cache.
2008-08-22 07:24:18.238 Clearing Settings Cache.
2008-08-22 07:24:18.239 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'MythGame' and hostname = 'timmyth' ;
2008-08-22 07:24:18.240 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Game' AND action = 'TOGGLEFAV' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.241 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Game' AND action = 'INCSEARCH' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.242 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Game' AND action = 'INCSEARCHNEXT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.245 MSqlQuery: SELECT data FROM settings WHERE value = 'MythMovies.DatabaseVersion' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.265 Disabling Settings Cache.
2008-08-22 07:24:18.266 Clearing Settings Cache.
2008-08-22 07:24:18.266 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicDBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.267 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicDBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.267 Enabling Settings Cache.
2008-08-22 07:24:18.267 Clearing Settings Cache.
2008-08-22 07:24:18.316 Failed to run 'cdrecord --scanbus'
2008-08-22 07:24:18.321 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-08-22 07:24:18.325 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-08-22 07:24:18.326 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicLocation' AND hostname = 'timmyth'
2008-08-22 07:24:18.327 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicAudioDevice' AND hostname = 'timmyth'
2008-08-22 07:24:18.328 MSqlQuery: SELECT data FROM settings WHERE value = 'CDDevice' AND hostname = 'timmyth'
2008-08-22 07:24:18.329 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoLookupCD' AND hostname = 'timmyth'
2008-08-22 07:24:18.330 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoPlayCD' AND hostname = 'timmyth'
2008-08-22 07:24:18.331 MSqlQuery: SELECT data FROM settings WHERE value = 'KeyboardAccelerators' AND hostname = 'timmyth'
2008-08-22 07:24:18.331 MSqlQuery: SELECT data FROM settings WHERE value = 'TreeLevels' AND hostname = 'timmyth'
2008-08-22 07:24:18.332 MSqlQuery: SELECT data FROM settings WHERE value = 'ArtistTreeGroups' AND hostname = 'timmyth'
2008-08-22 07:24:18.333 MSqlQuery: SELECT data FROM settings WHERE value = 'NonID3FileNameFormat' AND hostname = 'timmyth'
2008-08-22 07:24:18.334 MSqlQuery: SELECT data FROM settings WHERE value = 'Ignore_ID3' AND hostname = 'timmyth'
2008-08-22 07:24:18.335 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicTagEncoding' AND hostname = 'timmyth'
2008-08-22 07:24:18.336 MSqlQuery: SELECT data FROM settings WHERE value = 'CDWriterEnabled' AND hostname = 'timmyth'
2008-08-22 07:24:18.336 MSqlQuery: SELECT data FROM settings WHERE value = 'CDWriterDevice' AND hostname = 'timmyth'
2008-08-22 07:24:18.337 MSqlQuery: SELECT data FROM settings WHERE value = 'CDDiskSize' AND hostname = 'timmyth'
2008-08-22 07:24:18.338 MSqlQuery: SELECT data FROM settings WHERE value = 'CDCreateDir' AND hostname = 'timmyth'
2008-08-22 07:24:18.339 MSqlQuery: SELECT data FROM settings WHERE value = 'CDWriteSpeed' AND hostname = 'timmyth'
2008-08-22 07:24:18.339 MSqlQuery: SELECT data FROM settings WHERE value = 'CDBlankType' AND hostname = 'timmyth'
2008-08-22 07:24:18.342 MSqlQuery: SELECT data FROM settings WHERE value = 'PlayMode' AND hostname = 'timmyth'
2008-08-22 07:24:18.343 MSqlQuery: SELECT data FROM settings WHERE value = 'ResumeMode' AND hostname = 'timmyth'
2008-08-22 07:24:18.344 MSqlQuery: SELECT data FROM settings WHERE value = 'MaxSearchResults' AND hostname = 'timmyth'
2008-08-22 07:24:18.345 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicShowRatings' AND hostname = 'timmyth'
2008-08-22 07:24:18.346 MSqlQuery: SELECT data FROM settings WHERE value = 'ShowWholeTree' AND hostname = 'timmyth'
2008-08-22 07:24:18.346 MSqlQuery: SELECT data FROM settings WHERE value = 'ListAsShuffled' AND hostname = 'timmyth'
2008-08-22 07:24:18.347 MSqlQuery: SELECT data FROM settings WHERE value = 'IntelliRatingWeight' AND hostname = 'timmyth'
2008-08-22 07:24:18.348 MSqlQuery: SELECT data FROM settings WHERE value = 'IntelliPlayCountWeight' AND hostname = 'timmyth'
2008-08-22 07:24:18.349 MSqlQuery: SELECT data FROM settings WHERE value = 'IntelliLastPlayWeight' AND hostname = 'timmyth'
2008-08-22 07:24:18.350 MSqlQuery: SELECT data FROM settings WHERE value = 'IntelliRandomWeight' AND hostname = 'timmyth'
2008-08-22 07:24:18.351 MSqlQuery: SELECT data FROM settings WHERE value = 'VisualMode' AND hostname = 'timmyth'
2008-08-22 07:24:18.351 MSqlQuery: SELECT data FROM settings WHERE value = 'VisualCycleOnSongChange' AND hostname = 'timmyth'
2008-08-22 07:24:18.401 MSqlQuery: SELECT data FROM settings WHERE value = 'VisualAlbumArtOnSongChange' AND hostname = 'timmyth'
2008-08-22 07:24:18.402 MSqlQuery: SELECT data FROM settings WHERE value = 'VisualRandomize' AND hostname = 'timmyth'
2008-08-22 07:24:18.403 MSqlQuery: SELECT data FROM settings WHERE value = 'VisualModeDelay' AND hostname = 'timmyth'
2008-08-22 07:24:18.404 MSqlQuery: SELECT data FROM settings WHERE value = 'VisualScaleWidth' AND hostname = 'timmyth'
2008-08-22 07:24:18.404 MSqlQuery: SELECT data FROM settings WHERE value = 'VisualScaleHeight' AND hostname = 'timmyth'
2008-08-22 07:24:18.406 MSqlQuery: SELECT data FROM settings WHERE value = 'ParanoiaLevel' AND hostname = 'timmyth'
2008-08-22 07:24:18.407 MSqlQuery: SELECT data FROM settings WHERE value = 'FilenameTemplate' AND hostname = 'timmyth'
2008-08-22 07:24:18.408 MSqlQuery: SELECT data FROM settings WHERE value = 'NoWhitespace' AND hostname = 'timmyth'
2008-08-22 07:24:18.409 MSqlQuery: SELECT data FROM settings WHERE value = 'PostCDRipScript' AND hostname = 'timmyth'
2008-08-22 07:24:18.409 MSqlQuery: SELECT data FROM settings WHERE value = 'EjectCDAfterRipping' AND hostname = 'timmyth'
2008-08-22 07:24:18.410 MSqlQuery: SELECT data FROM settings WHERE value = 'EncoderType' AND hostname = 'timmyth'
2008-08-22 07:24:18.411 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultRipQuality' AND hostname = 'timmyth'
2008-08-22 07:24:18.412 MSqlQuery: SELECT data FROM settings WHERE value = 'Mp3UseVBR' AND hostname = 'timmyth'
2008-08-22 07:24:18.412 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Play music' and hostname = 'timmyth' ;
2008-08-22 07:24:18.413 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Select music playlists' and hostname = 'timmyth' ;
2008-08-22 07:24:18.413 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Rip CD' and hostname = 'timmyth' ;
2008-08-22 07:24:18.414 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Scan music' and hostname = 'timmyth' ;
2008-08-22 07:24:18.414 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Show Music Miniplayer' and hostname = 'timmyth' ;
2008-08-22 07:24:18.414 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'DELETE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.415 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'NEXTTRACK' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.416 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'PREVTRACK' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.417 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'FFWD' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.418 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'RWND' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.418 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'PAUSE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.419 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'PLAY' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.419 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'STOP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.420 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'VOLUMEDOWN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.421 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'VOLUMEUP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.422 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'MUTE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.423 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'CYCLEVIS' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.423 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'BLANKSCR' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.439 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'THMBUP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.440 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'THMBDOWN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.441 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'REFRESH' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.441 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'FILTER' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.442 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'INCSEARCH' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.443 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'INCSEARCHNEXT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.444 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'SPEEDUP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.444 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Music' AND action = 'SPEEDDOWN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.445 Registering MythMusic Media Handler 1/2 as a media handler for MEDIATYPE_MIXED
2008-08-22 07:24:18.445 Registering MythMusic Media Handler 2/2 as a media handler for MEDIATYPE_MMUSIC, ext(ogg,mp3,aac,flac)
2008-08-22 07:24:18.445 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-08-22 07:24:18.445 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicLocation' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.446 MSqlQuery: SELECT data FROM settings WHERE value = 'Ignore_ID3' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.447 MSqlQuery: SELECT data FROM settings WHERE value = 'CDDevice' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.447 MSqlQuery: SELECT data FROM settings WHERE value = 'PlayMode' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.448 MSqlQuery: SELECT data FROM settings WHERE value = 'RepeatMode' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.449 MSqlQuery: SELECT data FROM settings WHERE value = 'ResumeMode' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.449 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicLastPlayDelay' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.450 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicLastPlayDelay' AND hostname IS NULL;
2008-08-22 07:24:18.451 MSqlQuery: SELECT data FROM settings WHERE value = 'MusicAutoShowPlayer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.455 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'MythNews' and hostname = 'timmyth' ;
2008-08-22 07:24:18.455 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'News' AND action = 'RETRIEVENEWS' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.456 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'News' AND action = 'FORCERETRIEVE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.456 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'News' AND action = 'CANCEL' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.461 Disabling Settings Cache.
2008-08-22 07:24:18.461 Clearing Settings Cache.
2008-08-22 07:24:18.462 MSqlQuery: SELECT data FROM settings WHERE value = 'PhoneDBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.463 MSqlQuery: SELECT data FROM settings WHERE value = 'PhoneDBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.463 Enabling Settings Cache.
2008-08-22 07:24:18.463 Clearing Settings Cache.
2008-08-22 07:24:18.484 MSqlQuery: SELECT data FROM settings WHERE value = 'SipRegisterWithProxy' AND hostname = 'timmyth'
2008-08-22 07:24:18.485 MSqlQuery: SELECT data FROM settings WHERE value = 'SipProxyName' AND hostname = 'timmyth'
2008-08-22 07:24:18.486 MSqlQuery: SELECT data FROM settings WHERE value = 'SipProxyAuthName' AND hostname = 'timmyth'
2008-08-22 07:24:18.487 MSqlQuery: SELECT data FROM settings WHERE value = 'SipProxyAuthPassword' AND hostname = 'timmyth'
2008-08-22 07:24:18.488 MSqlQuery: SELECT data FROM settings WHERE value = 'MySipName' AND hostname = 'timmyth'
2008-08-22 07:24:18.489 MSqlQuery: SELECT data FROM settings WHERE value = 'SipAutoanswer' AND hostname = 'timmyth'
2008-08-22 07:24:18.489 MSqlQuery: SELECT data FROM settings WHERE value = 'SipBindInterface' AND hostname = 'timmyth'
2008-08-22 07:24:18.490 MSqlQuery: SELECT data FROM settings WHERE value = 'SipLocalPort' AND hostname = 'timmyth'
2008-08-22 07:24:18.491 MSqlQuery: SELECT data FROM settings WHERE value = 'NatTraversalMethod' AND hostname = 'timmyth'
2008-08-22 07:24:18.492 MSqlQuery: SELECT data FROM settings WHERE value = 'NatIpAddress' AND hostname = 'timmyth'
2008-08-22 07:24:18.493 MSqlQuery: SELECT data FROM settings WHERE value = 'AudioLocalPort' AND hostname = 'timmyth'
2008-08-22 07:24:18.494 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoLocalPort' AND hostname = 'timmyth'
2008-08-22 07:24:18.494 MSqlQuery: SELECT data FROM settings WHERE value = 'MicrophoneDevice' AND hostname = 'timmyth'
2008-08-22 07:24:18.495 MSqlQuery: SELECT data FROM settings WHERE value = 'CodecPriorityList' AND hostname = 'timmyth'
2008-08-22 07:24:18.496 MSqlQuery: SELECT data FROM settings WHERE value = 'PlayoutAudioCall' AND hostname = 'timmyth'
2008-08-22 07:24:18.497 MSqlQuery: SELECT data FROM settings WHERE value = 'PlayoutVideoCall' AND hostname = 'timmyth'
2008-08-22 07:24:18.497 MSqlQuery: SELECT data FROM settings WHERE value = 'WebcamDevice' AND hostname = 'timmyth'
2008-08-22 07:24:18.498 MSqlQuery: SELECT data FROM settings WHERE value = 'TxResolution' AND hostname = 'timmyth'
2008-08-22 07:24:18.499 MSqlQuery: SELECT data FROM settings WHERE value = 'TransmitFPS' AND hostname = 'timmyth'
2008-08-22 07:24:18.500 MSqlQuery: SELECT data FROM settings WHERE value = 'TransmitBandwidth' AND hostname = 'timmyth'
2008-08-22 07:24:18.501 MSqlQuery: SELECT data FROM settings WHERE value = 'CaptureResolution' AND hostname = 'timmyth'
2008-08-22 07:24:18.502 MSqlQuery: SELECT data FROM settings WHERE value = 'TimeToAnswer' AND hostname = 'timmyth'
2008-08-22 07:24:18.502 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultVxmlUrl' AND hostname = 'timmyth'
2008-08-22 07:24:18.503 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultVoicemailPrompt' AND hostname = 'timmyth'
2008-08-22 07:24:18.504 MSqlQuery: SELECT data FROM settings WHERE value = 'TTSVoice' AND hostname = 'timmyth'
2008-08-22 07:24:18.505 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '0' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.506 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '1' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.506 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '2' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.507 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '3' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.507 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '4' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.508 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '5' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.509 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '6' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.511 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '7' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.512 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '8' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.513 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = '9' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.513 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'HASH' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.514 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'STAR' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.514 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'Up' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.515 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'Down' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.516 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'Left' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.516 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'Right' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.517 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'VOLUMEDOWN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.518 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'VOLUMEUP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.519 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'MUTE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.520 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'ZOOMIN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.521 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'ZOOMOUT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.526 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'FULLSCRN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.526 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'HANGUP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.527 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Phone' AND action = 'LOOPBACK' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.528 MSqlQuery: SELECT data FROM settings WHERE value = 'MySipName' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.528 MSqlQuery: SELECT data FROM settings WHERE value = 'SipRegisterWithProxy' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.528 MSqlQuery: SELECT data FROM settings WHERE value = 'SipProxyAuthName' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.529 MSqlQuery: SELECT intid,nickname,url FROM phonedirectory WHERE directory = "My MythTVs" and firstname = "Local Myth Host" and surname = "timmyth";
2008-08-22 07:24:18.536 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'MythStream' and hostname = 'timmyth' ;
2008-08-22 07:24:18.537 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'PAUSE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.537 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'VOLDN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.538 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'VOLUP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.539 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'AVINC' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.540 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'AVDEC' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.541 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'MUTE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.541 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'END' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.542 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'FULLSCREEN' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.544 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'FORWARD' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.545 MSqlQuery: SELECT data FROM settings WHERE value = 'SipLocalPort' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.545 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'REWIND' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.548 MSqlQuery: SELECT data FROM settings WHERE value = 'SipBindInterface' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.548 MSqlQuery: SELECT data FROM settings WHERE value = 'NatTraversalMethod' AND hostname = 'timmyth' ;
SIP listening on IP Address 192.168.1.3:5060 NAT address 192.168.1.3
2008-08-22 07:24:18.549 MSqlQuery: SELECT data FROM settings WHERE value = 'SipProxyName' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.550 MSqlQuery: SELECT data FROM settings WHERE value = 'SipProxyAuthPassword' AND hostname = 'timmyth' ;
SIP: Cannot register; proxy, username or password not set
2008-08-22 07:24:18.550 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'MARK' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.551 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'STOREMARKED' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.551 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'INSPECT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.552 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'DUMP' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.553 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'SPEECH' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.562 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'EDITITEM' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.562 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'RECORD' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.563 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'STOPRECORD' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.563 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Stream' AND action = 'STOPALLRECORD' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.571 Disabling Settings Cache.
2008-08-22 07:24:18.571 Clearing Settings Cache.
2008-08-22 07:24:18.572 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.DBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.572 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.DBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.573 MSqlQuery: SELECT data FROM settings WHERE value = 'DVDDBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.574 MSqlQuery: SELECT data FROM settings WHERE value = 'DVDDBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.575 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoDBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.575 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoDBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.576 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.DBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.576 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.DBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.576 Enabling Settings Cache.
2008-08-22 07:24:18.576 Clearing Settings Cache.
2008-08-22 07:24:18.581 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoStartupDir' AND hostname = 'timmyth'
2008-08-22 07:24:18.582 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoArtworkDir' AND hostname = 'timmyth'
2008-08-22 07:24:18.583 MSqlQuery: SELECT data FROM settings WHERE value = 'Default MythVideo View' AND hostname = 'timmyth'
2008-08-22 07:24:18.584 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoListUnknownFiletypes' AND hostname = 'timmyth'
2008-08-22 07:24:18.585 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoBrowserNoDB' AND hostname = 'timmyth'
2008-08-22 07:24:18.586 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoGalleryNoDB' AND hostname = 'timmyth'
2008-08-22 07:24:18.587 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoTreeNoDB' AND hostname = 'timmyth'
2008-08-22 07:24:18.588 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoTreeLoadMetaData' AND hostname = 'timmyth'
2008-08-22 07:24:18.588 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoNewBrowsable' AND hostname = 'timmyth'
2008-08-22 07:24:18.589 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.sort_ignores_case' AND hostname = 'timmyth'
2008-08-22 07:24:18.590 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.db_folder_view' AND hostname = 'timmyth'
2008-08-22 07:24:18.591 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.VideoTreeRemember' AND hostname = 'timmyth'
2008-08-22 07:24:18.592 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.ImageCacheSize' AND hostname = 'timmyth'
2008-08-22 07:24:18.592 MSqlQuery: SELECT data FROM settings WHERE value = 'DVDDeviceLocation' AND hostname = 'timmyth'
2008-08-22 07:24:18.593 MSqlQuery: SELECT data FROM settings WHERE value = 'VCDDeviceLocation' AND hostname = 'timmyth'
2008-08-22 07:24:18.594 MSqlQuery: SELECT data FROM settings WHERE value = 'DVDOnInsertDVD' AND hostname = 'timmyth'
2008-08-22 07:24:18.595 MSqlQuery: SELECT data FROM settings WHERE value = 'DVDDriveSpeed' AND hostname = 'timmyth'
2008-08-22 07:24:18.596 MSqlQuery: SELECT data FROM settings WHERE value = 'EnableDVDBookmark' AND hostname = 'timmyth'
2008-08-22 07:24:18.685 MSqlQuery: SELECT data FROM settings WHERE value = 'DVDBookmarkPrompt' AND hostname = 'timmyth'
2008-08-22 07:24:18.686 MSqlQuery: SELECT data FROM settings WHERE value = 'DVDBookmarkDays' AND hostname = 'timmyth'
2008-08-22 07:24:18.687 MSqlQuery: SELECT data FROM settings WHERE value = 'MovieListCommandLine' AND hostname = 'timmyth'
2008-08-22 07:24:18.688 MSqlQuery: SELECT data FROM settings WHERE value = 'MoviePosterCommandLine' AND hostname = 'timmyth'
2008-08-22 07:24:18.688 MSqlQuery: SELECT data FROM settings WHERE value = 'MovieDataCommandLine' AND hostname = 'timmyth'
2008-08-22 07:24:18.689 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoGalleryColsPerPage' AND hostname = 'timmyth'
2008-08-22 07:24:18.690 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoGalleryRowsPerPage' AND hostname = 'timmyth'
2008-08-22 07:24:18.691 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoGallerySubtitle' AND hostname = 'timmyth'
2008-08-22 07:24:18.692 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoDefaultParentalLevel' AND hostname = 'timmyth'
2008-08-22 07:24:18.693 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoAdminPassword' AND hostname = 'timmyth'
2008-08-22 07:24:18.693 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoAdminPasswordThree' AND hostname = 'timmyth'
2008-08-22 07:24:18.694 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoAdminPasswordTwo' AND hostname = 'timmyth'
2008-08-22 07:24:18.695 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoAggressivePC' AND hostname = 'timmyth'
2008-08-22 07:24:18.696 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.ParentalLevelFromRating' AND hostname = 'timmyth'
2008-08-22 07:24:18.697 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.AutoR2PL1' AND hostname = 'timmyth'
2008-08-22 07:24:18.697 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.AutoR2PL2' AND hostname = 'timmyth'
2008-08-22 07:24:18.698 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.AutoR2PL3' AND hostname = 'timmyth'
2008-08-22 07:24:18.699 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.AutoR2PL4' AND hostname = 'timmyth'
2008-08-22 07:24:18.700 MSqlQuery: SELECT data FROM settings WHERE value = 'VideoDefaultPlayer' AND hostname = 'timmyth'
2008-08-22 07:24:18.701 MSqlQuery: SELECT data FROM settings WHERE value = 'mythdvd.DVDPlayerCommand' AND hostname = 'timmyth'
2008-08-22 07:24:18.702 MSqlQuery: SELECT data FROM settings WHERE value = 'VCDPlayerCommand' AND hostname = 'timmyth'
2008-08-22 07:24:18.704 MSqlQuery: SELECT data FROM settings WHERE value = 'DVDRipLocation' AND hostname = 'timmyth'
2008-08-22 07:24:18.705 MSqlQuery: SELECT data FROM settings WHERE value = 'TitlePlayCommand' AND hostname = 'timmyth'
2008-08-22 07:24:18.706 MSqlQuery: SELECT data FROM settings WHERE value = 'SubTitleCommand' AND hostname = 'timmyth'
2008-08-22 07:24:18.707 MSqlQuery: SELECT data FROM settings WHERE value = 'TranscodeCommand' AND hostname = 'timmyth'
2008-08-22 07:24:18.707 MSqlQuery: SELECT data FROM settings WHERE value = 'MTDPort' AND hostname = 'timmyth'
2008-08-22 07:24:18.708 MSqlQuery: SELECT data FROM settings WHERE value = 'MTDNiceLevel' AND hostname = 'timmyth'
2008-08-22 07:24:18.709 MSqlQuery: SELECT data FROM settings WHERE value = 'MTDConcurrentTranscodes' AND hostname = 'timmyth'
2008-08-22 07:24:18.710 MSqlQuery: SELECT data FROM settings WHERE value = 'MTDRipSize' AND hostname = 'timmyth'
2008-08-22 07:24:18.711 MSqlQuery: SELECT data FROM settings WHERE value = 'MTDLogFlag' AND hostname = 'timmyth'
2008-08-22 07:24:18.712 MSqlQuery: SELECT data FROM settings WHERE value = 'MTDac3Flag' AND hostname = 'timmyth'
2008-08-22 07:24:18.712 MSqlQuery: SELECT data FROM settings WHERE value = 'MTDxvidFlag' AND hostname = 'timmyth'
2008-08-22 07:24:18.718 MSqlQuery: SELECT data FROM settings WHERE value = 'mythvideo.TrustTranscodeFRDetect' AND hostname = 'timmyth'
2008-08-22 07:24:18.719 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'MythVideo' and hostname = 'timmyth' ;
2008-08-22 07:24:18.719 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Video Manager' and hostname = 'timmyth' ;
2008-08-22 07:24:18.719 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Video Browser' and hostname = 'timmyth' ;
2008-08-22 07:24:18.720 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Video Listings' and hostname = 'timmyth' ;
2008-08-22 07:24:18.720 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Video Gallery' and hostname = 'timmyth' ;
2008-08-22 07:24:18.721 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'FILTER' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.721 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'DELETE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.722 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'BROWSE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.723 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'INCPARENT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.723 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'DECPARENT' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.724 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'HOME' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.725 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Video' AND action = 'END' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.726 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Play DVD' and hostname = 'timmyth' ;
2008-08-22 07:24:18.726 Registering MythDVD DVD Media Handler as a media handler for MEDIATYPE_DVD
2008-08-22 07:24:18.726 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Play VCD' and hostname = 'timmyth' ;
2008-08-22 07:24:18.726 Registering MythDVD VCD Media Handler as a media handler for MEDIATYPE_VCD
2008-08-22 07:24:18.727 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Rip DVD' and hostname = 'timmyth' ;
2008-08-22 07:24:18.731 Disabling Settings Cache.
2008-08-22 07:24:18.731 Clearing Settings Cache.
2008-08-22 07:24:18.732 MSqlQuery: SELECT data FROM settings WHERE value = 'WeatherDBSchemaVer' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.732 MSqlQuery: SELECT data FROM settings WHERE value = 'WeatherDBSchemaVer' AND hostname IS NULL;
2008-08-22 07:24:18.732 Enabling Settings Cache.
2008-08-22 07:24:18.732 Clearing Settings Cache.
2008-08-22 07:24:18.733 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'MythWeather' and hostname = 'timmyth' ;
2008-08-22 07:24:18.734 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Weather' AND action = 'PAUSE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.735 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Weather' AND action = 'SEARCH' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.735 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Weather' AND action = 'NEXTSEARCH' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.736 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Weather' AND action = 'UPDATE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.737 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Weather' AND action = 'DELETE' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.738 MSqlQuery: SELECT data FROM settings WHERE value = 'weatherbackgroundfetch' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.739 MSqlQuery: SELECT data FROM settings WHERE value = 'weatherbackgroundfetch' AND hostname IS NULL;
2008-08-22 07:24:18.740 MSqlQuery: SELECT data FROM settings WHERE value = 'EnableXbox' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.742 MSqlQuery: SELECT data FROM settings WHERE value = 'idleTimeoutSecs' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.743 MSqlQuery: SELECT data FROM settings WHERE value = 'idleTimeoutSecs' AND hostname IS NULL;
2008-08-22 07:24:18.744 MSqlQuery: SELECT data FROM settings WHERE value = 'NetworkControlEnabled' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.745 MSqlQuery: SELECT data FROM settings WHERE value = 'Theme' AND hostname = 'timmyth' ;
2008-08-22 07:24:18.746 MSqlQuery: SELECT data FROM settings WHERE value = 'AllowQuitShutdown' AND hostname = 'timmyth' ;
2008-08-22 07:24:20.675 MSqlQuery: SELECT data FROM settings WHERE value = 'Language' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.309 MSqlQuery: SELECT data FROM settings WHERE value = 'CustomFilters' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.310 MSqlQuery: SELECT data FROM settings WHERE value = 'CustomFilters' AND hostname IS NULL;
2008-08-22 07:24:23.310 MSqlQuery: SELECT data FROM settings WHERE value = 'ChannelFormat' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.311 MSqlQuery: SELECT data FROM settings WHERE value = 'TimeFormat' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.312 MSqlQuery: SELECT data FROM settings WHERE value = 'ShortDateFormat' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.312 MSqlQuery: SELECT data FROM settings WHERE value = 'SmartChannelChange' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.313 MSqlQuery: SELECT data FROM settings WHERE value = 'IndividualMuteControl' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.314 MSqlQuery: SELECT data FROM settings WHERE value = 'UseArrowAccels' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.315 MSqlQuery: SELECT data FROM settings WHERE value = 'PersistentBrowseMode' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.315 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDGeneralTimeout' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.316 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDProgramInfoTimeout' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.317 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoCommercialSkip' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.317 MSqlQuery: SELECT data FROM settings WHERE value = 'TryUnflaggedSkip' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.318 MSqlQuery: SELECT data FROM settings WHERE value = 'TryUnflaggedSkip' AND hostname IS NULL;
2008-08-22 07:24:23.319 MSqlQuery: SELECT data FROM settings WHERE value = 'SmartForward' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.321 MSqlQuery: SELECT data FROM settings WHERE value = 'StickyKeys' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.322 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewReposTime' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.323 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewReverse' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.324 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed0' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.324 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed0' AND hostname IS NULL;
2008-08-22 07:24:23.325 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed1' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.326 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed1' AND hostname IS NULL;
2008-08-22 07:24:23.326 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed2' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.327 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed2' AND hostname IS NULL;
2008-08-22 07:24:23.327 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed3' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.328 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed3' AND hostname IS NULL;
2008-08-22 07:24:23.328 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed4' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.329 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed4' AND hostname IS NULL;
2008-08-22 07:24:23.330 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed5' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.330 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed5' AND hostname IS NULL;
2008-08-22 07:24:23.331 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed6' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.331 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed6' AND hostname IS NULL;
2008-08-22 07:24:23.332 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed7' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.332 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed7' AND hostname IS NULL;
2008-08-22 07:24:23.333 MSqlQuery: SELECT data FROM settings WHERE value = 'VbiFormat' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.338 MSqlQuery: SELECT data FROM settings WHERE value = 'VbiFormat' AND hostname IS NULL;
2008-08-22 07:24:23.339 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiSizeForTV' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.340 MSqlQuery: SELECT data FROM settings WHERE value = 'UseVideoModes' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.341 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.342 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2008-08-22 07:24:23.343 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.344 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname IS NULL;
2008-08-22 07:24:23.344 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.345 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname IS NULL;
2008-08-22 07:24:23.428 MythEvent: PLAYBACK_START timmyth
2008-08-22 07:24:23.429 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.430 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname IS NULL;
2008-08-22 07:24:23.431 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.432 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname IS NULL;
2008-08-22 07:24:23.432 MythSocket(b30b0e90:23): new socket
2008-08-22 07:24:23.433 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.434 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname IS NULL;
2008-08-22 07:24:23.434 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname = 'timmyth' ;
2008-08-22 07:24:23.435 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname IS NULL;
2008-08-22 07:24:23.435 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-08-22 07:24:23.436 MythSocket(b30a89d8:24): new socket
2008-08-22 07:24:23.436 MythSocket(b30a89d8:24): attempting connect() to (127.0.0.1:6543)
2008-08-22 07:24:23.436 MythSocket(b30a89d8:24): state change Idle -> Connected
2008-08-22 07:24:23.436 write -> 24 21      MYTH_PROTO_VERSION 40
2008-08-22 07:24:23.437 read  <- 24 13      ACCEPT[]:[]40
2008-08-22 07:24:23.439 Using protocol version 40
2008-08-22 07:24:23.439 write -> 24 21      ANN Monitor timmyth 0
2008-08-22 07:24:23.444 read  <- 24 2       OK
2008-08-22 07:24:23.444 MythSocket(b30b0e90:23): attempting connect() to (127.0.0.1:6543)
2008-08-22 07:24:23.444 MythSocket(b30b0e90:23): state change Idle -> Connected
2008-08-22 07:24:23.445 write -> 23 21      ANN Monitor timmyth 1
2008-08-22 07:24:23.448 read  <- 23 2       OK
2008-08-22 07:24:23.448 MythSocket: readyread thread start
2008-08-22 07:24:23.449 MythSocket(b30b0e90:23): UpRef: 1
2008-08-22 07:24:23.449 write -> 24 23      GET_FREE_RECORDER_COUNT
2008-08-22 07:24:23.449 read  <- 24 1       0
2008-08-22 07:24:23.449 write -> 24 26      QUERY_RECORDINGS Recording
2008-08-22 07:24:23.454 read  <- 24 1       0
2008-08-22 07:24:23.456 TV Error: Failed to get recording show list
2008-08-22 07:24:23.458 MythEvent: PLAYBACK_END timmyth
2008-08-22 07:24:25.015 MSqlQuery: SELECT data FROM settings WHERE value = 'NoPromptOnExit' AND hostname = 'timmyth' ;
2008-08-22 07:24:25.016 write -> 24 35      QUERY_IS_ACTIVE_BACKEND[]:[]timmyth
2008-08-22 07:24:25.016 read  <- 24 4       TRUE
2008-08-22 07:24:25.017 MSqlQuery: SELECT data FROM settings WHERE value = 'OverrideExitMenu' AND hostname = 'timmyth' ;
Destroying SipFsm object 
2008-08-22 07:24:27.051 MSqlQuery: DELETE FROM settings WHERE value = 'PlayMode' AND hostname = 'timmyth' ;
2008-08-22 07:24:27.052 MSqlQuery: INSERT INTO settings (value,data,hostname) VALUES ( 'PlayMode', 'none', 'timmyth' );
2008-08-22 07:24:27.052 Clearing Settings Cache.
2008-08-22 07:24:27.052 Clearing Settings Cache.
2008-08-22 07:24:27.053 MSqlQuery: DELETE FROM settings WHERE value = 'RepeatMode' AND hostname = 'timmyth' ;
2008-08-22 07:24:27.053 MSqlQuery: INSERT INTO settings (value,data,hostname) VALUES ( 'RepeatMode', 'all', 'timmyth' );
2008-08-22 07:24:27.053 Clearing Settings Cache.
2008-08-22 07:24:27.053 Clearing Settings Cache.
2008-08-22 07:24:27.054 MSqlQuery: DELETE FROM settings WHERE value = 'MusicAutoShowPlayer' AND hostname = 'timmyth' ;
2008-08-22 07:24:27.055 MSqlQuery: INSERT INTO settings (value,data,hostname) VALUES ( 'MusicAutoShowPlayer', '1', 'timmyth' );
2008-08-22 07:24:27.055 Clearing Settings Cache.
2008-08-22 07:24:27.055 Clearing Settings Cache.
2008-08-22 07:24:27.059 MythSocket(b30a89d8:24): DownRef: -1
2008-08-22 07:24:27.062 MythSocket(b30a89d8:24): state change Connected -> Idle
2008-08-22 07:24:27.062 MythSocket(b30a89d8:-1): delete socket
2008-08-22 07:24:27.062 MythSocket(b30b0e90:23): DownRef: 0
2008-08-22 07:24:27.063 MythSocket(b30b0e90:23): DownRef: -1
2008-08-22 07:24:27.063 MythSocket(b30b0e90:23): state change Connected -> Idle
2008-08-22 07:24:27.063 MythSocket(b30b0e90:-1): delete socket
2008-08-22 07:24:27.064 Deleting UPnP client...
2008-08-22 07:24:27.064 WorkerThread:Run - Exiting: HTTP_WorkerThread
2008-08-22 07:24:27.065 UPnp - Destructor
2008-08-22 07:24:27.065 UPnp::CleanUp() - disabling SSDP notifications
2008-08-22 07:24:27.066 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-08-22 07:24:27.066 SSDP::ProcessNotify
DescURL=http://192.168.1.3:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7::upnp:rootdevice
Cache  =max-age=3600
2008-08-22 07:24:27.133 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-08-22 07:24:27.134 SSDP::ProcessNotify
DescURL=http://192.168.1.3:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7::upnp:rootdevice
Cache  =max-age=3600
2008-08-22 07:24:27.134 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-08-22 07:24:27.134 SSDP::ProcessNotify
DescURL=http://192.168.1.3:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7
USN    =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7
Cache  =max-age=3600
2008-08-22 07:24:27.187 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-08-22 07:24:27.188 SSDP::ProcessNotify
DescURL=http://192.168.1.3:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7
USN    =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7
Cache  =max-age=3600
2008-08-22 07:24:27.188 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-08-22 07:24:27.188 SSDP::ProcessNotify
DescURL=http://192.168.1.3:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-08-22 07:24:27.213 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-08-22 07:24:27.214 SSDP::ProcessNotify
DescURL=http://192.168.1.3:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2008-08-22 07:24:27.214 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-08-22 07:24:27.214 SSDP::ProcessNotify
DescURL=http://192.168.1.3:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-08-22 07:24:27.233 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2008-08-22 07:24:27.233 SSDP::ProcessNotify
DescURL=http://192.168.1.3:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:f09bda86-6d26-4e20-b19d-1d4e89d2eda7::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2008-08-22 07:24:27.236 UPnp::CleanUp() - deleted SSDP
2008-08-22 07:24:27.345 MythSocket: readyread thread exit
```

---

### Post by NT4usB on 2008-08-22
It goes by pretty fast too. Looks like we missed the part where you tried liveTV and it failed. Gotta be real quick with the ctrl+c to kill the frontend soon as liveTV stops.
Try this instead:```
mythtv -v all
```
No need to start the frontend. This should (try to) start liveTV all by itself.
Then, soon as it dies you will see what broke in the terminal.

---

### Post by jasontu on 2008-08-25
Nice!  I'll try it when I get home.

---

### Post by OffAxis on 2008-08-25
what's also helpful is bypassing mythtv entirely (to see if it's a configuration problem with myth or something else)

```
mplayer /dev/video0
```

where video0 =  your video card input (might be video1, etc)

will play whatever is coming in your pvr-150

---

### Post by jasontu on 2008-08-25
I didn't even know that I could do that through MPLAYER!  If mPlayer can also record what's coming through I'll just use that.  

I only care to get this to work so I can digitize some VHS tapes and burn them to DVDs.  

I'm starting to hate MythTV.  I don't even own a TV antenna or cable!  All I really need this for is to get some VHS tapes into the computer so I can burn them to DVD.

---

### Post by wolfen69 on 2008-08-25
during setup, did you choose mpeg2 decoder? the default is V4L. run setup again, and double check that.

---

### Post by jasontu on 2008-08-25
I think it's on V4L.  Is that wrong?

---

### Post by OffAxis on 2008-08-25
> I only care to get this to work so I can digitize some VHS tapes and burn them to DVDs. 

If that's all you're doing then you don't need mythtv setup. Just use mplayer or vlc (I like vlc's interface a little better for that type of job).

you can also just go with a 

```
cat /dev/video0 > file.mpg
```

to save the stream to a file directly. Ctrl+C will break the redirect, and then 

```
mplayer /path/to/file.mpg
```

to view it.

---

### Post by OffAxis on 2008-08-25
> I think it's on V4L. Is that wrong?
yes; it should be on mpeg-2 decoder.

---

### Post by wolfen69 on 2008-08-25
it will say "mpeg2 pvr x50 500" or something like that. choose it. V4L decoders will not work with hauppauge pvr's. i responded a few weeks back to you about this very issue. i guess you didnt get it. you should be able to watch tv now.

---

### Post by OffAxis on 2008-08-25
By the way, the last time I checked the dvd-burning feature of MythArchive had some issues, so you would need to do some tweaking or exit mythtv and burn the tracks with brasero or k3b or something. Recordings get put in 
**/var/lib/mythtv/recordings/**

If you're up for doing the tweaks here's a thread on the subject:
[http://ubuntuforums.org/showthread.php?t=863812](http://ubuntuforums.org/showthread.php?t=863812)

---

### Post by NT4usB on 2008-08-25
MythTV is really hateful if install doesn't go good and you have to debug. Took me a solid month to get it going when I first installed it two years ago. That was v18. and you had to build it all manually. 
You don't need (or want) it if all you're doing is ripping VHS.
I've used kino to grab video off a camcorder. Might work for a VCR... worth trying, anyway.

aarg... 
jasontu, go back and edit your second post and change the quote to code and /code so it will put all that output in a window. (code in square brackets before and /code in square brackets after)

---

### Post by jasontu on 2008-08-25
```
2008-08-25 18:30:16.556 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-25 18:30:16.566 XScreenSaver support enabled
2008-08-25 18:30:16.566 DPMS is active.
2008-08-25 18:30:16.567 Empty LocalHostName.
2008-08-25 18:30:16.567 Using localhost value of timmyth
2008-08-25 18:30:16.568 MCP::DefaultUPnP() - No default UPnP backend
2008-08-25 18:30:16.579 New DB connection, total: 1
2008-08-25 18:30:16.586 Connected to database 'mythconverg' at host: localhost
2008-08-25 18:30:16.587 Closing DB connection named 'DBManager0'
2008-08-25 18:30:16.587 Clearing Settings Cache.
2008-08-25 18:30:16.604 Primary screen 0.
2008-08-25 18:30:16.604 Connected to database 'mythconverg' at host: localhost
2008-08-25 18:30:16.606 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.606 Using screen 0, 1366x768 at 0,0
2008-08-25 18:30:16.607 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.607 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname IS NULL;
2008-08-25 18:30:16.608 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.608 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname IS NULL;
2008-08-25 18:30:16.609 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.609 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2008-08-25 18:30:16.610 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.611 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname IS NULL;
2008-08-25 18:30:16.611 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.614 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname IS NULL;
2008-08-25 18:30:16.619 Enabling Settings Cache.
2008-08-25 18:30:16.620 Clearing Settings Cache.
2008-08-25 18:30:16.621 MSqlQuery: SELECT data FROM settings WHERE value = 'Theme' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.622 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeResolution' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.623 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeRefreshRate' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.624 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeRefreshRate' AND hostname IS NULL;
2008-08-25 18:30:16.625 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeForceAspect' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.625 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeForceAspect' AND hostname IS NULL;
2008-08-25 18:30:16.779 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.780 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname IS NULL;
2008-08-25 18:30:16.780 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.781 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname IS NULL;
2008-08-25 18:30:16.782 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeHeight' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.782 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeHeight' AND hostname IS NULL;
2008-08-25 18:30:16.783 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeResolution' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.784 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeRefreshRate' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.784 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeForceAspect' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.785 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeResolution0' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.785 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeResolution0' AND hostname IS NULL;
2008-08-25 18:30:16.786 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeWidth0' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.786 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeWidth0' AND hostname IS NULL;
2008-08-25 18:30:16.787 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeHeight0' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.788 MSqlQuery: SELECT data FROM settings WHERE value = 'VidModeHeight0' AND hostname IS NULL;
2008-08-25 18:30:16.788 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeResolution0' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.789 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeRefreshRate0' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.793 MSqlQuery: SELECT data FROM settings WHERE value = 'TVVidModeForceAspect0' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.795 max_width: 1366 max_height: 768
2008-08-25 18:30:16.795 MSqlQuery: SELECT data FROM settings WHERE value = 'UseVideoModes' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.796 Primary screen 0.
2008-08-25 18:30:16.797 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.797 Using screen 0, 1366x768 at 0,0
2008-08-25 18:30:16.797 MSqlQuery: SELECT data FROM settings WHERE value = 'Style' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.822 Switching to square mode (Mythbuntu-8.04)
2008-08-25 18:30:16.823 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.823 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname IS NULL;
2008-08-25 18:30:16.823 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.824 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname IS NULL;
2008-08-25 18:30:16.824 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.824 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2008-08-25 18:30:16.825 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.825 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname IS NULL;
2008-08-25 18:30:16.825 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.826 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname IS NULL;
2008-08-25 18:30:16.827 MSqlQuery: SELECT data FROM settings WHERE value = 'MenuTheme' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.828 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontBig' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.829 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontMedium' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.830 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontSmall' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.831 MSqlQuery: SELECT data FROM settings WHERE value = 'AudioOutputDevice' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.959 MSqlQuery: SELECT data FROM settings WHERE value = 'ThemePainter' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.959 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-08-25 18:30:16.960 lirc_init failed for mythtv, see preceding messages
2008-08-25 18:30:16.960 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jason/.mythtv/joystickmenurc
2008-08-25 18:30:16.960 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'UP' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.961 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'DOWN' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.961 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'LEFT' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.962 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'RIGHT' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.962 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'SELECT' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.963 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'ESCAPE' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.963 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'MENU' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.964 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'INFO' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.964 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PAGEUP' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.965 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PAGEDOWN' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.965 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'PREVVIEW' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.966 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'NEXTVIEW' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.966 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'HELP' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.966 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = 'EJECT' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.967 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '0' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.967 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '1' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.968 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '2' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.968 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '3' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.972 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '4' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.973 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '5' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.974 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '6' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.974 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '7' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.974 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '8' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.975 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Global' AND action = '9' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.976 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFonTweak' AND hostname = 'timmyth' ;
2008-08-25 18:30:16.976 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFonTweak' AND hostname IS NULL;
2008-08-25 18:30:16.977 MSqlQuery: SELECT data FROM settings WHERE value = 'HideMouseCursor' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.554 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGEUP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.554 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGEDOWN' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.555 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGETOP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.555 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGEMIDDLE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.555 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGEBOTTOM' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.556 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'DELETE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.556 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'PLAYBACK' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.557 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'TOGGLERECORD' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.557 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'DAYLEFT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.558 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'DAYRIGHT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.558 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGELEFT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.559 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGERIGHT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.559 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'TOGGLEFAV' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.559 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'TOGGLEEPGORDER' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.560 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'GUIDE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.560 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'FINDER' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.561 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'NEXTFAV' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.561 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'CHANUPDATE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.562 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'VOLUMEDOWN' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.562 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'VOLUMEUP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.563 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'MUTE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.566 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'RANKINC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.568 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'RANKDEC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.568 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'UPCOMING' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.569 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'DETAILS' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.569 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'VIEWCARD' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.570 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'VIEWINPUT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.570 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'CUSTOMEDIT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.571 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'CHANGERECGROUP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.571 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Frontend' AND action = 'CHANGEGROUPVIEW' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.572 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'CLEAROSD' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.572 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'PAUSE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.573 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'DELETE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.573 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SEEKFFWD' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.573 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SEEKRWND' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.574 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'ARBSEEK' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.574 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'CHANNELUP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.575 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'CHANNELDOWN' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.575 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTFAV' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.576 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVCHAN' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.576 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPFFWD' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.576 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPRWND' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.577 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPBKMRK' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.577 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'FFWDSTICKY' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.582 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'RWNDSTICKY' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.583 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTSOURCE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.583 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVSOURCE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.584 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTINPUT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.585 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTCARD' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.585 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SKIPCOMMERCIAL' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.586 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SKIPCOMMBACK' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.587 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPSTART' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.587 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEBROWSE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.588 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLERECORD' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.589 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEFAV' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.589 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'VOLUMEDOWN' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.590 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'VOLUMEUP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.590 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'MUTE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.591 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEPIPMODE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.592 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEPIPWINDOW' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.592 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SWAPPIP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.593 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEASPECT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.593 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEFILL' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.594 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLECC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.595 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLETTC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.595 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLESUBTITLE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.596 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLECC608' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.596 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLECC708' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.597 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLETTM' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.597 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTAUDIO_0' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.597 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTAUDIO_1' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.598 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTSUBTITLE_0' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.598 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTSUBTITLE_1' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.599 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC608_0' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.599 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC608_1' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.600 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC608_2' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.600 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC608_3' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.601 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC708_0' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.601 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC708_1' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.602 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC708_2' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.602 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC708_3' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.603 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTAUDIO' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.603 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVAUDIO' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.604 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTSUBTITLE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.604 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVSUBTITLE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.605 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTCC608' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.605 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVCC608' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.605 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTCC708' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.606 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVCC708' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.606 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTCC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.607 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTSCAN' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.607 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'QUEUETRANSCODE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.608 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SPEEDINC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.608 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SPEEDDEC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.619 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'ADJUSTSTRETCH' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.619 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'STRETCHINC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.620 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'STRETCHDEC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.620 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLESTRETCH' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.621 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEAUDIOSYNC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.621 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEPICCONTROLS' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.622 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLECHANCONTROLS' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.623 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLERECCONTROLS' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.623 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEEDIT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.624 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'CYCLECOMMSKIPMODE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.624 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'GUIDE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.625 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'FINDER' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.625 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLESLEEP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.626 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'PLAY' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.627 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPPREV' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.627 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPREC' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.628 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'VIEWSCHEDULED' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.628 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SIGNALMON' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.629 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPTODVDROOTMENU' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.630 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'EXITSHOWNOPROMPTS' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.630 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'SCREENSHOT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.631 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'MENURED' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.631 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'MENUGREEN' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.632 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'MENUYELLOW' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.632 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'MENUBLUE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.633 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'TEXTEXIT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.633 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'MENUTEXT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.634 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Playback' AND action = 'MENUEPG' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.634 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Editing' AND action = 'CLEARMAP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.635 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Editing' AND action = 'INVERTMAP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.636 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Editing' AND action = 'LOADCOMMSKIP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.636 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Editing' AND action = 'NEXTCUT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.637 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Editing' AND action = 'PREVCUT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.637 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Editing' AND action = 'BIGJUMPREW' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.638 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Editing' AND action = 'BIGJUMPFWD' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.638 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'TV Editing' AND action = 'TOGGLEEDIT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.639 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'NEXTPAGE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.639 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'PREVPAGE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.640 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'NEXTSUBPAGE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.640 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'PREVSUBPAGE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.641 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'TOGGLETT' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.641 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENURED' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.642 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUGREEN' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.642 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUYELLOW' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.643 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUBLUE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.643 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUWHITE' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.644 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'TOGGLEBACKGROUND' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.645 MSqlQuery: SELECT keylist, description FROM keybindings WHERE context = 'Teletext Menu' AND action = 'REVEAL' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.671 New DB connection, total: 2
2008-08-25 18:30:17.671 Connected to database 'mythconverg' at host: localhost
2008-08-25 18:30:17.672 MSqlQuery: SELECT data FROM settings WHERE value = 'CustomFilters' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.673 MSqlQuery: SELECT data FROM settings WHERE value = 'CustomFilters' AND hostname IS NULL;
2008-08-25 18:30:17.674 MSqlQuery: SELECT data FROM settings WHERE value = 'ChannelFormat' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.675 MSqlQuery: SELECT data FROM settings WHERE value = 'TimeFormat' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.676 MSqlQuery: SELECT data FROM settings WHERE value = 'ShortDateFormat' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.677 MSqlQuery: SELECT data FROM settings WHERE value = 'SmartChannelChange' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.677 MSqlQuery: SELECT data FROM settings WHERE value = 'IndividualMuteControl' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.678 MSqlQuery: SELECT data FROM settings WHERE value = 'UseArrowAccels' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.679 MSqlQuery: SELECT data FROM settings WHERE value = 'PersistentBrowseMode' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.680 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDGeneralTimeout' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.681 MSqlQuery: SELECT data FROM settings WHERE value = 'OSDProgramInfoTimeout' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.682 MSqlQuery: SELECT data FROM settings WHERE value = 'AutoCommercialSkip' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.683 MSqlQuery: SELECT data FROM settings WHERE value = 'TryUnflaggedSkip' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.684 MSqlQuery: SELECT data FROM settings WHERE value = 'TryUnflaggedSkip' AND hostname IS NULL;
2008-08-25 18:30:17.685 MSqlQuery: SELECT data FROM settings WHERE value = 'SmartForward' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.685 MSqlQuery: SELECT data FROM settings WHERE value = 'StickyKeys' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.686 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewReposTime' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.687 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewReverse' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.688 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed0' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.689 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed0' AND hostname IS NULL;
2008-08-25 18:30:17.690 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed1' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.690 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed1' AND hostname IS NULL;
2008-08-25 18:30:17.691 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed2' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.692 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed2' AND hostname IS NULL;
2008-08-25 18:30:17.692 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed3' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.693 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed3' AND hostname IS NULL;
2008-08-25 18:30:17.694 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed4' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.694 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed4' AND hostname IS NULL;
2008-08-25 18:30:17.695 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed5' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.696 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed5' AND hostname IS NULL;
2008-08-25 18:30:17.696 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed6' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.697 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed6' AND hostname IS NULL;
2008-08-25 18:30:17.698 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed7' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.698 MSqlQuery: SELECT data FROM settings WHERE value = 'FFRewSpeed7' AND hostname IS NULL;
2008-08-25 18:30:17.699 MSqlQuery: SELECT data FROM settings WHERE value = 'VbiFormat' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.699 MSqlQuery: SELECT data FROM settings WHERE value = 'VbiFormat' AND hostname IS NULL;
2008-08-25 18:30:17.700 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiSizeForTV' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.874 MythEvent: PLAYBACK_START timmyth
2008-08-25 18:30:17.875 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.876 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname IS NULL;
2008-08-25 18:30:17.877 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.877 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname IS NULL;
2008-08-25 18:30:17.878 MythSocket(81ff100:14): new socket
2008-08-25 18:30:17.879 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.879 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendReconnectWaitTime' AND hostname IS NULL;
2008-08-25 18:30:17.880 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname = 'timmyth' ;
2008-08-25 18:30:17.881 MSqlQuery: SELECT data FROM settings WHERE value = 'WOLbackendConnectRetry' AND hostname IS NULL;
2008-08-25 18:30:17.881 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-08-25 18:30:17.881 MythSocket(824a568:15): new socket
2008-08-25 18:30:17.881 MythSocket(824a568:15): attempting connect() to (127.0.0.1:6543)
2008-08-25 18:30:17.882 MythSocket(824a568:15): state change Idle -> Connected
2008-08-25 18:30:17.882 write -> 15 21      MYTH_PROTO_VERSION 40
2008-08-25 18:30:17.883 read  <- 15 13      ACCEPT[]:[]40
2008-08-25 18:30:17.883 Using protocol version 40
2008-08-25 18:30:17.883 write -> 15 21      ANN Monitor timmyth 0
2008-08-25 18:30:17.889 read  <- 15 2       OK
2008-08-25 18:30:17.890 MythSocket(81ff100:14): attempting connect() to (127.0.0.1:6543)
2008-08-25 18:30:17.890 MythSocket(81ff100:14): state change Idle -> Connected
2008-08-25 18:30:17.890 write -> 14 21      ANN Monitor timmyth 1
2008-08-25 18:30:17.894 read  <- 14 2       OK
2008-08-25 18:30:17.894 MythSocket: readyread thread start
2008-08-25 18:30:17.894 MythSocket(81ff100:14): UpRef: 1
2008-08-25 18:30:17.895 write -> 15 23      GET_FREE_RECORDER_COUNT
2008-08-25 18:30:17.895 read  <- 15 1       0
2008-08-25 18:30:17.895 write -> 15 26      QUERY_RECORDINGS Recording
2008-08-25 18:30:17.900 read  <- 15 1       0
2008-08-25 18:30:17.902 TV Error: Failed to get recording show list
2008-08-25 18:30:17.904 MythEvent: PLAYBACK_END timmyth
2008-08-25 18:30:17.904 MythSocket(824a568:15): DownRef: -1
2008-08-25 18:30:17.904 MythSocket(824a568:15): state change Connected -> Idle
2008-08-25 18:30:17.905 MythSocket(824a568:-1): delete socket
2008-08-25 18:30:17.905 MythSocket(81ff100:14): DownRef: 0
2008-08-25 18:30:17.905 MythSocket(81ff100:14): DownRef: -1
2008-08-25 18:30:17.905 MythSocket(81ff100:14): state change Connected -> Idle
2008-08-25 18:30:17.905 MythSocket(81ff100:-1): delete socket
2008-08-25 18:30:17.929 MythSocket: readyread thread exit
```

Here is the output using the mythtv -v all command.  I'll give copying the output from Mplayer or VLC a try and report back.

---

### Post by jasontu on 2008-08-25
Setting Mythbuntu to MPEG2 x50 yielded the same result, but maybe I need to fiddle with it more.

vlc or mplayer /dev/video0 yields a result but that result is static.  I'm not sure why.  I tested the VCR on a TV and it worked just fine.  Do I need to set up something with the capture card?

Thanks for all your help everyone.  I hope you are not losing patience with me.

---

### Post by OffAxis on 2008-08-26
> vlc or mplayer /dev/video0 yields a result but that result is static. I'm not sure why.
hmm. That's peculiar...

Do you mean static as in 'unchanging'? (like a single frame capture?) or static like electromagnetic interference?
Whole picture or just a few scan lines?

Is it on the video only, or audio as well?

It could be a bad connection or EM interference (electrical power, fluorescent lighting)

> I tested the VCR on a TV and it worked just fine.
Did you use the same cable (coaxial?)?

---

### Post by jasontu on 2008-08-26
By static I mean I got the interference/white snow/fuzz sound effect.  Audio and video.

When I connected it to the TV, I did use the same cable.

---

### Post by OffAxis on 2008-08-26
Is this the PVR-150 with the singe coax out connection or the MCE PVR-150 with the multitude of RCA connectors?

---

### Post by newlinux on 2008-08-26
are you sure video0 is your pvr-150.

what does:
```

dmesg | grep video

```
return?

As for what you want to do, I'd skip mythtv and just use the command line and the at command would be useful too. For some examples:

[http://ubuntuforums.org/showthread.php?t=431793](http://ubuntuforums.org/showthread.php?t=431793)

---

### Post by jasontu on 2008-08-27
it yields:

```
[   44.211391] Boot video device is 0000:01:00.0
[   57.340578] Linux video capture interface: v2.00
[   59.365376] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   59.365405] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   59.365476] ivtv0: Registered device video24 for encoder PCM (320 kB)

```

If I touch the cable connecting the PCI card and the VCR the screen of static does change (similar to adjusting a TV antenna), but it does not get close to a picture it is supposed to.

Thanks

---

### Post by rlongfield on 2008-09-16
Just wondering if you were able to figure out the static problem with the PVR-150. I am experiencing the same problem here but with a Sat STB. I have the receiver connected via coax, I did a Dmesg like the post advises and indeed the PVR-150 is my video0 mpeg-2 capture device. When I do a mplayer /dev/video0 I get static just like Jasontu. I have a PVR-150 card not a MCE version, it only has a coax in, no RCA jacks.
If I had to guess I would say that the PVR-150 is not tuned to channel 3.

---

### Post by jasontu on 2008-09-16
I still haven't been able to figure this problem out.  I have been busy being hit with Hurricane Ike.  Lawl.  Seriously though.  This has me completely stumped.  I get white snow static, so obviously I am getting some kind of signal... just no signal that translates into me seeing the VHS I have connected to it.

---

### Post by rlongfield on 2008-09-16
I'm getting the white snow thing as well which makes me think it is a problem with the tuner not being set to channel 3. It reminds me of when I would have the TV set to some channel other than 3 and turn the VCR on to watch a movie, same static.
I've been searching on Google to see if I can find how to set the Hauppauge tuner to channel 3 but I have had no luck so far.

---

### Post by ReddogOne on 2008-09-16
> **jasontu said:**
>  because the options to select one of them appear at various stages of the easy 302,812 step process of setting up Mythbuntu.

Totolly agree with hte 302,812 comment... much more complicated than needed. Look [here]("http://parker1.co.uk/mythtv_ubuntu.php") for blindingly simple instructions about 12 steps so a saving of 302,800 on most installation instructions :D

You probably want to use the "DVB DTV Capture Card (v3.x)" rather than the screen mentioned above to select the card... or give it a go and see what happens.

---

### Post by NT4usB on 2008-09-16
> **rlongfield said:**
> ...ching on Google to see if I can find how to set the Hauppauge tuner to channel 3 but I have had no luck so far.
Open two terminals. 
In one:```
mplayer -vo xv /dev/video0
```and in the other:
```
ivtv-tune -c # -d /dev/video0
``` where #=channel number and your device is at /video0
May have to sudo it, I dunno...

*copied from, and credit to: [http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html](http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html)

---

### Post by rlongfield on 2008-09-17
Hey thanks NT4usB for that tip. I'll have to give it a try when I get back home, I did switch my input to RCA and in Myth I was able to change the input to composite and it works perfectly now.
I'll give NT4usB tip a try just for information sake.

---

### Post by jasontu on 2008-09-19
Oh jeez thank you, rlongfield and NT4usB!

I'm finally getting video from my VHS! I just had to change the channel to 3 apparently!

One slight problem remains... sound.  I can't hear anything.  I'm using the RF cable for the connection.  Any ideas?

---

### Post by NT4usB on 2008-09-20
Are you still using MythTV? From the frontend, go to setup>setup>general on page 3 is configuration for sound.
output device and mixer device: 
Alsa:default
mixer controls: 
master

If not, double click the speaker to open volume controls look to see if master and pcm are not muted and up a bit.

---


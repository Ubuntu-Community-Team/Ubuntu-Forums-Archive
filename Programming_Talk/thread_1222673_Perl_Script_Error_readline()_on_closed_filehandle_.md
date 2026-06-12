---
title: "Perl Script Error: readline() on closed filehandle IN"
date: 2009-07-25
forum: Programming Talk
---

### Post by BryceHarding on 2009-07-25
I need help with a Perl script i found on this how to: [URL="http://www.edsalisbury.net/linux/how-to-copy-videos-from-a-series-3-tivo-to-ubuntu-linux/"]http://www.edsalisbury.net/linux/how-to-copy-videos-from-a-series-3-tivo-to-ubuntu-linux/
[/URL]

I am a total newb when it comes to perl scripting but have been able to follow along the instructions to get it working & resolved the dependencies for the required modules etc.

the problem now seems to be with the script it's self now. I am getting the following error: readline() on closed filehandle IN at /usr/local/bin/tivo_dump line 84.

It doesn't like the <IN> argument in the following While Loop:

```

# Load the file that has the previously saved programs
open(IN, $PROGRAMS_FILE);
while (<IN>)
{
    chop();
    push(@PREV, $_);
}
close (IN);
``` 

I get the feeling that the script is either reading a closed or non existant file or reading past the end of the file but I'm really not sure. I'm at the limits of what I am able to figure out without help but would appreciate any Ideas at all

Below is the full script:


```
#!/usr/bin/perl
# TiVo Dump
# Copy TiVo programs from a Series3 TiVo
# by Ed Salisbury (ed@edsalisbury.net)
# http://www.edsalisbury.net
# (c)2009 Ed Salisbury, Some Rights Reserved
#
# External Utilities Required:
# * curl
# * tivodecode
#
# External Perl Modules Required:
# * Net::TiVo
# * XML::Simple
# * Text::Unidecode;
#
# Usage:
# tivo_dump
#
# License:
# Except where otherwise noted, this work is licensed under Creative Commons
#   Attribution ShareAlike 3.0.
#
# You are free:
#   * to Share - to copy, distribute and transmit the work
#   * to Remix - to adapt the work
#
# Under the following conditions:
#   * Attribution. You must attribute the work in the manner specified by the
#     author or licensor (but not in any way that suggests that they endorse
#     you or your use of the work).
#   * Share Alike. If you alter, transform, or build upon this work, you may
#     distribute the resulting work only under the same, similar or a
#     compatible license.
#   * For any reuse or distribution, you must make clear to others the license
#     terms of this work. The best way to do this is with a link to the
#     license's web page (http://creativecommons.org/licenses/by-sa/3.0/)
#   * Any of the above conditions can be waived if you get permission from the
#     copyright holder.
#   * Nothing in this license impairs or restricts the author's moral rights.
 
use warnings;
use strict;
use Net::TiVo;
use XML::Simple;
use utf8;
use Text::Unidecode;
 
sub fix_chars($);
 
# User-Configurable Variables
my $HOST = "192.168.1.105";      # Hostname/IP of the TiVo
my $MAK = "5924624918";       # The Media Access Key of the TiVo
my $VIDEO_DIR = "/home/bryce/Tivo"; # Where the programs get saved
my $COPY_SUGGESTIONS = 0; # If you want to copy "Suggested" programs, set this to 1
 
my $USER = "tivo";
my $TMPFILE = "/tmp/$$.xml";
my $PROGRAMS_FILE = "~/.tivo_programs";
$|++;
 
# External Utilities
my $CURL = "/usr/bin/curl";
my $TIVODECODE = "/usr/local/bin/tivodecode";
 
my @PREV;
 
# Connect to the TiVo
print "Connecting to TiVo at $HOST... ";
my $tivo = Net::TiVo->new(host => $HOST, mac => $MAK);
my @folders = $tivo->folders();
if (@folders)
{
    print "OK\n";
}
else
{
    print "FAIL\n";
    exit();
}
 
# Load the file that has the previously saved programs
open(IN, $PROGRAMS_FILE);
while (<IN>)
{
    chop();
    push(@PREV, $_);
}
close (IN);
 
# Go through each folder on the TiVo
foreach my $folder (@folders)
{
    foreach my $item ($folder->{'xmlref'}{'Item'})
    {
        foreach my $video (@$item)
        {
            # Only process videos, not folders
            if ($video->{'Links'}{'Content'}{'ContentType'} eq "video/x-tivo-raw-tts")
            {
                # Choose video type based on the icon
                if ($video->{'Links'}{'CustomIcon'} && $video->{'Links'}{'CustomIcon'}{'Url'} eq "urn:tivo:image:suggestion-recording" && !$COPY_SUGGESTIONS)
                {
                    next;
                }
                if ($video->{'Links'}{'CustomIcon'} &&
                   ($video->{'Links'}{'CustomIcon'}{'Url'} eq "urn:tivo:image:in-progress-transfer" ||
                    $video->{'Links'}{'CustomIcon'}{'Url'} eq "urn:tivo:image:in-progress-recording"))
                {
                   next;
                }
 
                # Get program and episode titles
                my $program_title = $video->{'Details'}{'Title'};
 
                if ($video->{'Details'}{'EpisodeTitle'})
                {
                    $program_title .= " - " . $video->{'Details'}{'EpisodeTitle'};
                }
 
                # Get Program ID and Video URL
                my $video_url = $video->{'Links'}{'Content'}{'Url'};
                my $program_id = $video->{'Details'}{'ProgramId'};
 
                if (!$program_id)
                {
                    next;
                }
 
                # If previously copied, skip
                if (grep /^$program_id$/, @PREV)
                {
                    print "Skipping $program_title.\n";
                    next;
                }
 
                # get details XML file
                print "Getting details for $program_title... ";
                my $details_xml = $video->{'Links'}{'TiVoVideoDetails'}{'Url'};
 
                system("$CURL --digest -s -k -u $USER:$MAK -c /tmp/cookies.txt -o $TMPFILE \"$details_xml\"");
                if (-f $TMPFILE)
                {
                    print "OK\nProcessing details file... ";
                    my $xml = XML::Simple->new();
                    my $doc = $xml->XMLin($TMPFILE);
                    my %meta;
                    my $filepath;
                    my $filename;
 
                    # Get rating and convert to proper form
                    $meta{'tvRating'} = $doc->{'showing'}{'tvRating'}{'content'};
                    if ($meta{'tvRating'})
                    {
                        if ($meta{'tvRating'} eq "Y_7") { $meta{'tvRating'} = 'x1'; }
                        elsif ($meta{'tvRating'} eq "PG") { $meta{'tvRating'} = 'x4'; }
                        elsif ($meta{'tvRating'} eq "_14") { $meta{'tvRating'} = 'x5'; }
                        else { $meta{'tvRating'} = "x7"; }
                    }
 
                    # Get other data
                    $meta{'vActor'} = $doc->{'showing'}{'program'}{'vActor'}{'element'};
                    $meta{'vDirector'} = $doc->{'showing'}{'program'}{'vDirector'}{'element'};
                    $meta{'vProgramGenre'} = $doc->{'showing'}{'program'}{'vProgramGenre'}{'element'};
                    $meta{'vSeriesGenre'} = $doc->{'showing'}{'program'}{'series'}{'vSeriesGenre'}{'element'};
                    $meta{'seriesTitle'} = $doc->{'showing'}{'program'}{'series'}{'seriesTitle'};
                    $meta{'title'} = $doc->{'showing'}{'program'}{'title'};
                    $meta{'isEpisode'} = $doc->{'showing'}{'program'}{'isEpisode'};
                    $meta{'originalAirDate'} = $doc->{'showing'}{'program'}{'originalAirDate'};
                    $meta{'episodeTitle'} = $doc->{'showing'}{'program'}{'episodeTitle'};
                    $meta{'description'} = $doc->{'showing'}{'program'}{'description'};
 
                    if (defined $meta{'description'})
                    {
                        $meta{'description'} =~ s/\s+Copyright.*$//;
                    }
 
                    # Process Titles
 
                    $meta{'episodeNumber'} = $doc->{'showing'}{'program'}{'episodeNumber'};
 
                    my $series_title = '';
                    my $episode_number = '';
                    my $episode_title = '';
                    my $title = '';
 
                    if ($meta{'seriesTitle'})
                    {
                        $series_title = fix_chars($meta{'seriesTitle'});
                    }
                    if ($meta{'episodeNumber'})
                    {
                        $episode_number = fix_chars($meta{'episodeNumber'});
                    }
                    if ($meta{'episodeTitle'})
                    {
                        $episode_title = fix_chars($meta{'episodeTitle'});
                    }
                    if ($meta{'title'})
                    {
                        $title = fix_chars($meta{'title'});
                    }
 
                    if ($series_title && $episode_number && $episode_title)
                    {
                        $filepath = "$VIDEO_DIR/$series_title";
                        $filename = "$filepath/$series_title - $episode_number - $episode_title";
                    }
                    elsif ($series_title && $episode_title)
                    {
                        $filepath = "$VIDEO_DIR/$series_title";
                        $filename = "$filepath/$series_title - $episode_title";
                    }
                    elsif ($title)
                    {
                        $filepath = "$VIDEO_DIR/$title";
                        $filename = "$filepath/$title";
                    }
                    else
                    {
                        $filepath = "$VIDEO_DIR";
                        $filename = "$filepath/Unknown";
                    }
                    print "OK\n";
 
                    unless (-d $filepath)
                    {
                        print "Path $filepath doesn't exist, creating... ";
                        mkdir($filepath);
                        if (-d $filepath)
                        {
                            print "OK\n";
                        }
                        else
                        {
                            print "FAIL\n";
                            exit;
                        }
                    }
 
                    # Get the video with curl
                    print "Getting video... ";
                    system("$CURL --digest -s -k -u $USER:$MAK -c /tmp/cookies.txt -o \"$filename.tivo\" \"$video_url\"");
                    if (-f "$filename.tivo")
                    {
                        my $filesize = (stat("$filename.tivo"))[7];
 
                        if ($filesize > 0)
                        {
                            print "OK\n";
 
                            # Convert to MPG
                            print "Converting video to MPG format... ";
                            system("$TIVODECODE -m $MAK -o \"$filename.mpg\" \"$filename.tivo\" > /dev/null 2>&1");
                            if (-f "$filename.mpg")
                            {
                                print "OK\n";
                                unlink "$filename.tivo";
                                open(OUT, ">>$PROGRAMS_FILE");
                                print OUT "$program_id\n";
                                close(OUT);
                            }
                            else
                            {
                                print "FAIL\n";
                                exit();
                            }
 
                            # Output metadata file
                            print "Outputting metadata... ";
                            open (OUT, ">$filename.mpg.txt");
 
                            foreach my $key (keys %meta)
                            {
                                if ($meta{$key})
                                {
                                    if ($meta{$key} =~ /^ARRAY/)
                                    {
                                        foreach my $item (@{$meta{$key}})
                                        {
                                            unless ($item =~ /^HASH/)
                                            {
                                                print OUT "$key : " . fix_chars($item) . "\n";
                                            }
                                        }
                                    }
                                    else
                                    {
                                        unless ($item =~ /^HASH/)
                                        {
                                            if ($key eq "originalAirDate")
                                            {
                                                print OUT "$key : " . $meta{$key} . "\n";
                                            }
                                            else
                                            {
                                                print OUT "$key : " . fix_chars($meta{$key}) . "\n";
                                            }
                                        }
                                    }
                                }
                            }
                            unlink($TMPFILE);
                            close(OUT);
                            print "OK\n";
                        }
                        else
                        {
                            print "FAIL\n";
                        }
                    }
                    else
                    {
                        print "FAIL\n";
                        exit();
                    }
                }
                else
                {
                    print "FAIL\n";
                    exit();
                }
            }
        }
    }
}
 
# Convert any offending characters
sub fix_chars($)
{
    my ($data) = @_;
 
    $data = unidecode($data);
 
    $data =~ s/\:/ -/g;
    $data =~ s/\//-/g;
    $data =~ s/\\/-/g;
    $data =~ s/\?/-/g;
    $data =~ s/\*/-/g;
 
    return $data;
}
```

---

### Post by ghostdog74 on 2009-07-25
so why don't you learn about Perl first before you start looking at people's code, since you are total noob?

---

### Post by Christmas on 2009-07-25
I'm a Perl beginner myself, but have you tried to read it like this:
```
# Load the file that has the previously saved programs
open (my $IN, "<", "$PROGRAMS_FILE") || die "Cannot open file for reading.\n";
while (<$IN>)
{
    chop();
    push(@PREV, $_);
}
close ($IN);
```
Are you sure the error is in this part of the code? It may be somewhere else.

---

### Post by EdSalisbury on 2009-08-21
I just happened to find this post, and then today someone posted a comment on my blog that there's a bug... Weird... Anyway, I fixed it and it should work for you now.  I had changed that at the last minute (basically you need to specify an actual path for the programs file -- '~' doesn't work for open().  The original blog post is at: [http://www.edsalisbury.net/linux/how-to-copy-videos-from-a-series-3-tivo-to-ubuntu-linux/](http://www.edsalisbury.net/linux/how-to-copy-videos-from-a-series-3-tivo-to-ubuntu-linux/)  Be sure to post there or email me at ed (at) edsalisbury (dot) net if you have any issues.

---


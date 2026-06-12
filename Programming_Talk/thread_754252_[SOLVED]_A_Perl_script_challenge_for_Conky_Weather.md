---
title: "[SOLVED] A Perl script challenge: for Conky Weather"
date: 2008-04-13
forum: Programming Talk
---

### Post by Bruce M. on 2008-04-13
[CENTER][SIZE="5"]**The Challenge:**[/SIZE]

**Write or re-write an existing perl weather script for conky.**[/CENTER]

It could very well be called: **Conky Weather Revisited V3** (see below)

I'm looking for a perl script writer that would like a challenge and help the thousands of conky users that would like to continue to have weather conditions and forecasts in their conkys running again.

It's "semi" offical that Conky's weather function doesn't work any more. Apparently Google's site is claiming the information as their own and have changed the xml format so the original **weather.sh** files don't work any more and the "perl" script that lvleph started, **weather.pl**, in [Conky Weather Revisited V2]("http://ubuntuforums.org/showthread.php?t=666842") is defunct as well. This is the one that could be re-written and it even has a True Type Font (weather.ttf) to use with it.

kaivalagi's [Conky Weather Python Scripts Based On Metar / Weather.com XOAP service]("http://ubuntuforums.org/showthread.php?t=750532") has potential, but when I see the shear number of execi calls I shudder. Take a look at my sig to see why my poor desktop shudders as well.

lvleph's perl script got a five day forecast with only two execi calls which is great for my old machine and faster ones as well.

I have found a great international site [Weather Underground]("http://wunderground.com") that would suit this very well. Each "city" is classified by an html page. IE: Buenos Aires, Argentina is :87582.html See it here: [BsAs]("http://www.wunderground.com/global/stations/87582.html?bannertypeclick=sunandmoontransblack")

 It has (in Imperial and Metric formats on the same page):
[LIST]
[*]Current weather
[*]5 day forecast
[*]An extended 7 day forecast
[*]Humidity
[*]Due Point
[*]Wind
[*]Pressure
[*]Visibilty
[*]UV
[*]Clouds
[*]Elevation
[/LIST]

Information for Flight Rules:
Flight Rule:  	VFR (SABE)
Wind Speed: 	18 mph / 30 km/h / 8.2 m/s
Wind Dir: 	270° (West)
Ceiling: 	10000 ft / 3048 m

Their [Terms of Service]("http://www.wunderground.com/members/tos.asp") for members, which is free, although the $10/year option is activated by default.

So I ask you: Any perl scripts writers out there want to take up the challenge? It doesn't have to be only one but if more than one wants to volunteer they should be willing to work together and I will certainly be available for testing purposes.

I can't program my way out of a wet paper bag, but I will do anything I can to help get this up and running.

[CENTER][SIZE="4"]**Any Takers?**[/SIZE][/CENTER]

Have a great day.
Bruce

---

### Post by nanotube on 2008-04-13
just a note to potential future "takers": there's a nice RSS feed from weather undeground that contains the current conditions as well as forecast info, which would be much easier to parse than the actual website. e.g., for buenos aires:
[http://rss.wunderground.com/auto/rss_full/global/stations/87582.xml?units=both](http://rss.wunderground.com/auto/rss_full/global/stations/87582.xml?units=both)
will give you the rss feed.

so the problem is even simpler than it looks. :)

---

### Post by Bruce M. on 2008-04-13
> **nanotube said:**
> just a note to potential future "takers": there's a nice RSS feed from weather undeground that contains the current conditions as well as forecast info, which would be much easier to parse than the actual website. e.g., for buenos aires:
[http://rss.wunderground.com/auto/rss_full/global/stations/87582.xml?units=both](http://rss.wunderground.com/auto/rss_full/global/stations/87582.xml?units=both)
will give you the rss feed.

so the problem is even simpler than it looks. :)

Where does one find the RSS feed there?

EDIT: I'm hoping this can be done for "everyone," not just Buenos Aires  :)

---

### Post by nanotube on 2008-04-13
> **Bruce M. said:**
> Where does one find the RSS feed there?

EDIT: I'm hoping this can be done for "everyone," not just Buenos Aires  :)

in the top right corner, there's a little line with "add to favorites", a green "ical" button, and a red "rss" button. the red rss button is it. :)

yes, it does appear a standard feature, available for all their locations.

---

### Post by Bruce M. on 2008-04-15
> **nanotube said:**
> in the top right corner, there's a little line with "add to favorites", a green "ical" button, and a red "rss" button. the red rss button is it. :)

yes, it does appear a standard feature, available for all their locations.

Thank you ... now if only we can get a volunteer or two   :)

---

### Post by unutbu on 2008-04-15
Here is my solution to the Perl script challenge.
I hope you enjoy using it as much as I've enjoyed making it.

This script owes its existence to lvleph's weather.pl
([http://ubuntuforums.org/showthread.php?t=666842](http://ubuntuforums.org/showthread.php?t=666842)). Not only did I take some of his code, I
also learned a lot by looking at how he did things. Data-mining html as he did is not easy -- I tried doing the same for wunderground and had a script working only to find that the organization of the tables changes depending on your location! Ack! Doh! hehe... 

This script also owns its existence to
Bruce M. for posting the challenge that got me interested. Thanks Bruce! 

Like kaivalagi,
my solution is based on Weather.com's XOAP service. I tried registering this morning, but
for some reason they never emailed me my partner ID and license key, so I was
waiting around, totally bummed out, when I bumped into kaivalagi's python script
([http://ubuntuforums.org/showpost.php?p=4708045&postcount=10](http://ubuntuforums.org/showpost.php?p=4708045&postcount=10)) and saw his ID and key just
sitting there. So, naturally, like two Mauna Loa dark chocolate covered macadamia nuts, the temptation was just too great to resist. Thanks kaivalagi! 

If anyone can send me the SDK I'd be much obliged.

If doing cool things in a simple manner is a hallmark of genius then, well, I'm no genius
but Thomas Schnuecker and Larry Wall must be.  Thanks to Thomas Schnuecker,
<thomas@schnuecker.de> for writing the way cool Weather::Com perl module. Profound thanks
to Larry Wall for creating a language that both my computer and I can understand :).


**Step 0**: Install the weather.ttf font per lvleph's instructions at
[http://ubuntuforums.org/showthread.php?t=666842](http://ubuntuforums.org/showthread.php?t=666842)

**Step 1**: ```
sudo apt-get install libweather-com-perl
```

Weather.com made a change in their XOAP feed which breaks libweather-com-perl. Until the package is fixed, you'll have to fix it manually. Here's the fix:

```

sudo cp /usr/share/perl5/Weather/Com/Base.pm /usr/share/perl5/Weather/Com/Base-orig.pm
gksu gedit /usr/share/perl5/Weather/Com/Base.pm

```

Search and replace "&prod=xoap" with "&prod=xoap&link=xoap".
There should be two places where this change should be made. Save and exit. That's all you need to do. 

**Step 2**: Save this as 'ConkyWeather.pm'

```
=head1 NAME
=head1 NAME

ConkyWeather.pm

=cut

package ConkyWeather;
our @ISA=("Weather::Com::Finder");
use strict;
use warnings;
use Weather::Com::Finder;
use Encode;
my $PartnerId  = '1048871467';       # kaivalagi's
my $LicenseKey = '12daac2f3a67cb39'; # kaivalagi's
 
my $degree= encode_utf8( "\x{00B0}" ); 

my %weatherargs = (
    'partner_id' => $PartnerId,
    'license'    => $LicenseKey,
    );

sub new {
    my ($invocant,%opt)=@_;
    my $class=ref $invocant || $invocant;
    my $self={};
    bless $self,$class;

    $opt{units}='s' unless (defined($opt{units}));
    $opt{language}='en' unless (defined($opt{language}));
    $opt{debugmode}=0 unless (defined($opt{debugmode}));
    $opt{proxy}='' unless (defined($opt{proxy}));
    $opt{proxy_user}='' unless (defined($opt{proxy_user}));
    $opt{proxy_pass}='' unless (defined($opt{proxy_user}));

    my $weather_finder = Weather::Com::Finder->new(%weatherargs,%opt) || die;
    my $locations = $weather_finder->find($opt{loc});
    return unless (@{$locations});
    if (scalar @{$locations} > 1) {
	warn "More than one location found (see below). (Using " . $locations->[0]->name . "):\n\n";
	warn join ("\n", map {$_->name} @{$locations}) . "\n\n";
    }
    $self->{loc}=$locations->[0];
    die unless ($self->{loc});

    $self->{fc} = $self->{loc}->forecast();

    $self->{uodist} = $locations->[0]->units()->distance();
    $self->{uoprecip} = $locations->[0]->units()->precipitation();
    $self->{uopress} = $locations->[0]->units()->pressure();
    $self->{uotemp} = $degree;
    $self->{uospeed} = $locations->[0]->units()->speed();

    return $self;
}

sub name {
    my $self=shift;
    return $self->{loc}->name;
}

sub temp_unit {
    my $self=shift;
    return $self->{loc}->units->temperature;
}

sub latitude {
    my $self=shift;
    return $self->{loc}->latitude . "$degree";
}

sub longitude {
    my $self=shift;
    return $self->{loc}->longitude . "$degree";
}

sub time {
    my $self=shift;
    return $self->{loc}->localtime->time;
}

sub ampm_time {
    my $self=shift;
    return $self->{loc}->localtime->time_ampm;
}

sub timezone {
    my $self=shift;
    return $self->{loc}->timezone;
}

sub sunrise {
    my $self=shift;
    my $str=$self->{loc}->sunrise->time;
    $str=~s/^0//;
    return $str;
}

sub ampm_sunrise {
    my $self=shift;
    return $self->{loc}->sunrise->time_ampm;
}

sub sunset {
    my $self=shift;
    my $str=$self->{loc}->sunset->time;
    $str=~s/^0//;
    return $str;
}

sub ampm_sunset {
    my $self=shift;
    return $self->{loc}->sunset->time_ampm;
}

sub as_of {
    my $self=shift;
    return $self->{loc}->current_conditions->last_updated->time . " on " . $self->{loc}->current_conditions->last_updated->formatted('yyyy-mm-dd');
}

sub ampm_as_of {
    my $self=shift;
    return $self->{loc}->current_conditions->last_updated->time_ampm . " on " . $self->{loc}->current_conditions->last_updated->formatted('yyyy-mm-dd');
}

sub condition {
    my $self=shift;
    return $self->{loc}->current_conditions->description;
}

sub icon {
    my $str=shift;
    return '' unless ($str);
    if ($str=~m/Partly Cloudy/i){return "c";}
    elsif ($str=~m/Fair/i || $str=~m/Sun/i || $str=~m/Clear/i){return "A";}
    elsif ($str=~m/Cloud/i || $str=~m/Fog/i){return "e";}
    elsif ($str=~m/Storm/i || $str=~m/Thunder/i || $str=~m/T-/i){return "i";}
    elsif ($str=~m/Snow/i || $str=~m/Flurries/i || $str=~m/Wintry/i){return "k";}
    elsif ($str=~m/Rain/i || $str=~m/Drizzle/i){return "h";}
    elsif ($str=~m/Shower/i){return "g";}
    else {warn "Help! New symbol for '$str' needed!\n"; return ' ';}
}

sub condition_icon {
    my $self=shift;
    return icon($self->condition);
}

sub visibility {
    my $self=shift;
    return $self->{loc}->current_conditions->visibility . "$self->{uodist}";
}

sub temp {
    my $self=shift;
    return $self->{loc}->current_conditions->temperature . "$self->{uotemp}";
}

sub windchill {
    my $self=shift;
    return $self->{loc}->current_conditions->windchill . "$self->{uotemp}";
}

sub humidity {
    my $self=shift;
    return $self->{loc}->current_conditions->humidity . "\%";
}

sub dewpoint {
    my $self=shift;
    return $self->{loc}->current_conditions->dewpoint . "$self->{uotemp}";
}

sub windspeed {
    my $self=shift;
    return $self->{loc}->current_conditions->wind->speed . "$self->{uospeed}";
}

sub wind_dir_long {
    my $self=shift;
    return $self->{loc}->current_conditions->wind->direction_long;
}

sub wind_dir_short {
    my $self=shift;
    return $self->{loc}->current_conditions->wind->direction_short;
}

sub wind_dir_deg {
    my $self=shift;
    return $self->{loc}->current_conditions->wind->direction_degrees . "$degree";
}

sub max_gust {
    my $self=shift;
    my $max_gust=$self->{loc}->current_conditions->wind->maximum_gust;
    if (defined($max_gust) && ($max_gust ne 'N/A')) {
	return $self->{loc}->current_conditions->wind->maximum_gust . "$self->{uospeed}";
    } else {
	return ''
    }
}

sub uv {
    my $self=shift;
    return $self->{loc}->current_conditions->uv_index->index;
}

sub uv_description {
    my $self=shift;
    return $self->{loc}->current_conditions->uv_index->description;
}

sub pressure {
    my $self=shift;
    return $self->{loc}->current_conditions->pressure->pressure . "$self->{uopress}";
}

sub pressure_dir {
    my $self=shift;
    return $self->{loc}->current_conditions->pressure->tendency;
}

sub moon_phase {
    my $self=shift;
    return $self->{loc}->current_conditions->moon->description;
}

for my $daynum (0..4) {
    no strict "refs";
    my $method;

    $method="fc${daynum}_dow";
    *$method = sub {
	my $self=shift;
	return $self->{fc}->day($daynum)->date()->weekday();
    };

    $method="fc${daynum}_dow_short";
    *$method = sub {
	my $self=shift;
	my $str=$self->{fc}->day($daynum)->date()->weekday();
	my ($short)=($str=~m/^(.{3})/);
	return $short;
    };

    $method="fc${daynum}_high";
    *$method = sub {
	my $self=shift;
	return $self->{fc}->day($daynum)->high . "$self->{uotemp}";
    };

    $method="fc${daynum}_low";
    *$method = sub {
	my $self=shift;
	return $self->{fc}->day($daynum)->low . "$self->{uotemp}";
    };

    $method="fc${daynum}_sunrise";
    *$method = sub {
	my $self=shift;
	my $str=$self->{fc}->day($daynum)->sunrise->time;
	$str=~s/^0//;
	return $str;
    };

    $method="fc${daynum}_ampm_sunrise";
    *$method = sub {
	my $self=shift;
	return $self->{fc}->day($daynum)->sunrise->time_ampm;
    };

    $method="fc${daynum}_sunset";
    *$method = sub {
	my $self=shift;
	my $str=$self->{fc}->day($daynum)->sunset->time;
	$str=~s/^0//;
	return $str;
    };

    $method="fc${daynum}_ampm_sunset";
    *$method = sub {
	my $self=shift;
	return $self->{fc}->day($daynum)->sunset->time_ampm;
    };

    for my $dn_str (qw(day night)) {
	my $dn = ($dn_str eq 'day' ? '' : 'night_');

	$method="fc${daynum}_${dn}condition";
	*$method = sub {
	    my $self=shift;
	    die "no forecast object" unless (defined($self->{fc}));
	    die "no forecast for day $daynum" unless (defined($self->{fc}->day($daynum)));
	    if (defined($self->{fc}->day($daynum)->$dn_str)) {
		die "no forecast for conditions on day $daynum during the $dn_str" unless (defined($self->{fc}->day($daynum)->$dn_str->conditions));
		return $self->{fc}->day($daynum)->$dn_str->conditions; 
	    } else {
		return '';
	    }
	};

	$method="fc${daynum}_${dn}condition_icon";
	*$method = sub {
	    my $self=shift;
	    if (defined($self->{fc}->day($daynum)->$dn_str)) {
		die "no forecast for conditions on day $daynum during the $dn_str" unless (defined($self->{fc}->day($daynum)->$dn_str->conditions));
		return icon($self->{fc}->day($daynum)->$dn_str->conditions); 
	    } else {
		return '';
	    }
	};

	$method="fc${daynum}_${dn}humidity";
	*$method = sub {
	    my $self=shift;
	    if (defined($self->{fc}->day($daynum)->$dn_str)) {
		die "no forecast for humidity on day $daynum during the $dn_str" unless (defined($self->{fc}->day($daynum)->$dn_str->humidity));
		return $self->{fc}->day($daynum)->$dn_str->humidity . "\%"; 
	    } else {
		return '';
	    }
	};

	$method="fc${daynum}_${dn}precipitation";
	*$method = sub {
	    my $self=shift;
	    if (defined($self->{fc}->day($daynum)->$dn_str)) {
		die "no forecast for precipitation on day $daynum during the $dn_str" unless (defined($self->{fc}->day($daynum)->$dn_str->precipitation));
		return $self->{fc}->day($daynum)->$dn_str->precipitation . "\%"; 
	    } else {
		return '';
	    }
	};

	$method="fc${daynum}_${dn}windspeed";
	*$method = sub {
	    my $self=shift;
	    if (defined($self->{fc}->day($daynum)->$dn_str)) {
		return $self->{fc}->day($daynum)->$dn_str->wind->speed . "$self->{uospeed}";
	    } else {
		return '';
	    }
	};

	$method="fc${daynum}_${dn}max_gust";
	*$method = sub {
	    my $self=shift;
	    if (defined($self->{fc}->day($daynum)->$dn_str)) {
		my $max_gust=$self->{fc}->day($daynum)->$dn_str->wind->maximum_gust;
		if (defined($max_gust) && ($max_gust ne 'N/A')) {
		    return "$max_gust $self->{uospeed}";
		} else {
		    return '';
		}
	    } else {
		return '';
	    }
	};

	$method="fc${daynum}_${dn}wind_dir_long";
	*$method = sub {
	    my $self=shift;
	    if (defined($self->{fc}->day($daynum)->$dn_str)) {
		return $self->{fc}->day($daynum)->$dn_str->wind->direction_long;
	    } else {
		return '';
	    }
	};

	$method="fc${daynum}_${dn}wind_dir_short";
	*$method = sub {
	    my $self=shift;
	    if (defined($self->{fc}->day($daynum)->$dn_str)) {
		return $self->{fc}->day($daynum)->$dn_str->wind->direction_short;
	    } else {
		return '';
	    }
	};

	$method="fc${daynum}_${dn}wind_dir_deg";
	*$method = sub {
	    my $self=shift;
	    if (defined($self->{fc}->day($daynum)->$dn_str)) {
		return $self->{fc}->day($daynum)->$dn_str->wind->direction_degrees . "$degree";
	    } else {
		return '';
	    }
	};
    }
}

1;

=head1 Acknowledgements

This script owes its existence to lvleph's weather.pl
(http://ubuntuforums.org/showthread.php?t=666842). Not only did I take some of his code, I
also learned a lot by looking at how he did things. Data-mining html as he did is not easy
-- I tried doing the same for wunderground and had a script working only to find that the
organization of the pages changes depending on your location! Ack! Doh! hehe...

This script also owns its existence to Bruce M. for posting the challenge that got me
interested. Thanks Bruce!

Thanks to Thomas Schnuecker, <thomas@schnuecker.de> for writing the way cool Weather::Com
perl module. Profound thanks to Larry Wall for creating a language that both my computer
and I can understand :).

=cut

=head1 AUTHOR

 Unutbu
 2008-04-15

=cut


```

**Step 3**: Save this as 'conkyweather.pl'

```

#!/usr/bin/perl
use strict;
use warnings;
use lib ("$ENV{HOME}/bin");
use ConkyWeather;
use Getopt::Long;

my (
    $print_str,
    $units,
    $language,
    $loc,
    $example,
    $print_hilo,
    $code,
    );

GetOptions('loc=s' => \$loc,
	   'print=s' => \$print_str,
	   'units=s' => \$units,
	   'language=s' => \$language,
	   'example' => \$example,
	   'print_hilo' => \$print_hilo,
	   'code=s' => \$code,
    );

$loc='Buenos Aires, Argentina' unless (defined($loc));
$units='m' unless (defined($units));
$language='es' unless (defined($language));

my @key=qw(name latitude longitude time ampm_time timezone as_of ampm_as_of condition condition_icon visibility temp temp_unit windchill humidity dewpoint windspeed wind_dir_long wind_dir_short wind_dir_deg max_gust uv uv_description pressure pressure_dir moon_phase sunrise ampm_sunrise sunset ampm_sunset);
my @fc_key=qw(dow dow_short high low sunrise ampm_sunrise sunset ampm_sunset);
my @fc_dn_key=qw(condition condition_icon humidity precipitation windspeed max_gust wind_dir_long wind_dir_short wind_dir_deg);

my @all_keys;
my ($key,$val);

foreach $key (@key) {
    push(@all_keys,$key);
}

for my $daynum (0..4) {
    foreach my $fc (@fc_key) {
	$key="fc${daynum}_$fc";
	push(@all_keys,$key);
    }
    for my $dn_str (qw(day night)) {
	foreach my $fc (@fc_dn_key) {
	    my $dn = ($dn_str eq 'day' ? '' : 'night_');
	    $key="fc${daynum}_${dn}$fc";
	    push(@all_keys,$key);
	}
    }
}

if ($print_hilo) {
    $print_str="[fc1_high]     [fc2_high]     [fc3_high]     [fc4_high]\n[fc1_low]     [fc2_low]     [fc3_low]     [fc4_low]\n";
}

if ($print_str) {
    my $cw=ConkyWeather->new(loc=>$loc,language=>$language,units=>$units);
    foreach $key (@all_keys) {
	if ($print_str=~m/\[$key\]/) {
	    $val=$cw->$key;
	    $print_str=~s/\[$key\]/$val/g;
	}
    }
    $print_str=~s/\\n/\n/g;
    print "$print_str";
    exit;
}
if ($example) {
    my $cw=ConkyWeather->new(loc=>$loc,language=>$language,units=>$units);
    my ($key,$val);

    $key='keyword';
    $val='value';
    write;
    foreach $key (@all_keys) {
	$val=$cw->$key;
	$key='[' . $key . ']';
	write;
    }
    exit;

format =
@<<<<<<<<<<<<<<<<<<<<<<<<<< @<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
$key,                       $val
.

}

=head1 Acknowledgements

This script owes a lot to lvleph's weather.pl. I learned a
lot by looking at how he did things. I also his icon (cond_symb) code. Hehe... This script also owns its existence to Bruce M. for
posting the challenge that got me interested. Like kaivalagi, my solution is based on Weather.com's XOAP service. 

=cut

=head1 AUTHOR

 Unutbu
 2008-04-15

=cut


```

**Step 4**: Edit conkyweather.pl. Go down to line 28 or there abouts and change
```

$loc='Buenos Aires, Argentina' unless (defined($loc));
$units='m' unless (defined($units));
$language='es' unless (defined($language));

```

Changing $loc is obvious -- just be sure to specify your location by "city, country", not by any country code. $units can equal 'm' for metric and 's' for, um, imperial. (don't ask me why). $language uses the localization codes. 'en' is English, for example.

**Step 5**: Make conkyweather.pl executable.

```

chmod 755 conkyweather.pl
mkdir ~/bin
mv conkyweather.pl ConkyWeather.pm ~/bin 

```

Also make sure that ~/bin is in your $PATH.

**Step 6**: Adjust your .conkyrc to look something like this: 
The conkyweather-related lines are all in the TEXT section near the bottom and they all involve execi calls to conkyweather.pl. Pretty straight forward, I hope.


```
# UBUNTU-CONKY.

# Update interval in seconds
update_interval 1.0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override #try also 'normal' or 'desktop' 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 250 5
maximum_width 700

draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
draw_graph_borders no

use_xft yes
xftalpha 0.9
xftfont Bitstream Vera Sans Mono:size=12
uppercase no
override_utf8_locale yes
use_spacer no

stippled_borders 3
border_margin 9
border_width 10

# Gap between borders of screen and text
gap_x 10
gap_y 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
color1 orange

# Text alignment, other possible values are commented
alignment top_right

# stuff after 'TEXT' will be formatted on screen

TEXT
${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS 
${voffset -7}$hr $color
${execi 3600 conkyweather.pl --print "Feels like: [windchill]\nHumidity: [humidity]\nWind:  [windspeed] [wind_dir_short]\n"}

${voffset -70}$alignr${offset -50}${execi 3600 conkyweather.pl --print "[temp]"}
${voffset -15}$alignr${offset -50}${font weather:size=45}${execi 3600 conkyweather.pl --print "[condition_icon]"}$font

${voffset -25}${color1}$hr
${voffset -3}$alignc 4 DAY FORECAST 
${voffset -7}$hr $color
${execi 3600 conkyweather.pl --print "[fc1_dow_short]     [fc2_dow_short]     [fc3_dow_short]     [fc4_dow_short]"}
${font weather:size=30}${execi 3600 conkyweather.pl --print "[fc1_condition_icon]  [fc2_condition_icon]   [fc3_condition_icon]  [fc4_condition_icon]"}$color$font
${execi 3600 conkyweather.pl --print_hilo}

```

**Step 7**: Run conky.

**Step 8**: To find out about all keywords you can use to customize your .conkyrc,
run

```

conkyweather.pl --example

``` 

Look at the conkyweather.pl --print calls in the .conkyrc posted above to see how the keywords are used. All keywords should be enclosed in brackets [...].

(By the way, the command-line flags can be shortened if you like. For example, 
'conkyweather.pl --e' also works, and 'conkyweather.pl --p' is the same as 'conkyweather.pl --print'.)

---

### Post by Bruce M. on 2008-04-15
> **unutbu said:**
> Here is my solution to the Perl script challenge.
I hope you enjoy using it as much as I've enjoyed making it.


WoW! I'll take a look see tomorrow.
Cooking supper right now.

Thanks unutbu

---

### Post by Bruce M. on 2008-04-30
Hi unutbu,

Want to tank you for the script. It works as advertised.  :)

I know this is a looooooong tomorrow, but had a few problems here with computer and personal stuff.

Thank you for the script.
Bruce

---

### Post by unutbu on 2008-04-30
Bruce, thanks for trying it out. It's good to know it can work for others besides myself.

---

### Post by comprendrelinux on 2008-06-03
Hi Unutbu!

I did what you said but i'm getting this error message:

Can't use string ("0") as an ARRAY ref while "strict refs" in use at /home/joelle/bin/ConkyWeather.pm line 39

---

### Post by unutbu on 2008-06-03
Bonjour comprendrelinux,
Please post
```
grep '^$loc=' ~/bin/conkyweather.pl 
head -n44 ~/bin/ConkyWeather.pm  | tail -n10
/home/joelle/bin/conkyweather.pl --example

```
Is there any other output besides 
> Can't use string ("0") as an ARRAY ref while "strict refs" in use at /home/joelle/bin/ConkyWeather.pm line 39

---

### Post by comprendrelinux on 2008-06-03
Salut Unutbu!

grep '^$loc=' ~/bin/conkyweather.pl  gives:

```
 $loc='ASXX0112' unless (defined($loc));

```
head -n44 ~/bin/ConkyWeather.pm  | tail -n10 gives:
```

 my $weather_finder = Weather::Com::Finder->new(%weatherargs,%opt);
    my $locations = $weather_finder->find($opt{loc});
    return unless (@{$locations});
    if (scalar @{$locations} > 1) {
	warn "More than one location found (see below). (Using " . $locations->[0]->name . "):\n\n";
	warn join ("\n", map {$_->name} @{$locations}) . "\n\n";
    }
    $self->{loc}=$locations->[0];
    die unless ($self->{loc});

```

/home/joelle/bin/conkyweather.pl --example gives:
```

Can't use string ("0") as an ARRAY ref while "strict refs" in use at /home/joelle/bin/ConkyWeather.pm line 37

```

 There is no other output.

Joelle

---

### Post by unutbu on 2008-06-03
Change your $loc to

```
$loc='Sydney, Australia' unless (defined($loc));
```

---

### Post by comprendrelinux on 2008-06-03
This is my error message now:


```
More than one location found (see below). (Using Sydney Regional Office, Australia):

Sydney Regional Office, Australia
Sydney, Australia

Weather::Com::Location: ERROR Bad or missing query parameters in request.

```[/QUOTE]

---

### Post by unutbu on 2008-06-03
Hm. I was hoping you weren't going to get this error. 
Here is the fix.

```
sudo cp /usr/share/perl5/Weather/Com/Base.pm /usr/share/perl5/Weather/Com/Base-orig.pm
gksu gedit /usr/share/perl5/Weather/Com/Base.pm
```

Search and replace "&prod=xoap" with "&prod=xoap&link=xoap".
There should be two places where this change should be made.

---

### Post by comprendrelinux on 2008-06-03
Wow!This is great unutbu!I remember having to do such a change in my weather screenlet a while ago.

However, i'm getting another error message:
```
 Can't call method "weekday" on an undefined value at /home/joelle/bin/ConkyWeather.pm line 237, <DATA> line 1. 
```

---

### Post by comprendrelinux on 2008-06-03
Here is line 234-239 of ConkyWeather.pm
```
$method="fc${daynum}_dow_short";
    *$method = sub {
	my $self=shift;
	my $str=$self->{fc}->day($daynum)->date->weekday;
	my ($short)=($str=~m/^(.{3})/);
	return $short; 
```

---

### Post by unutbu on 2008-06-03
Unfortunately, Weather.com also cut back from 10-day forecasts down to 5-day forecasts. Changes had to be made in a number of places, so I edited my original post. You can download the new versions of ConkyWeather.pm and conkyweather.pl there.

---

### Post by comprendrelinux on 2008-06-03
It was the 5th day actually which didn't work. So i edited the conkyrc and ConkyWeather.pl file to a 4 day forecast and everything is perfect. Many thanks unutbu!!!

Two thumbs up for your post!!!

Cheers!
Joelle

---

### Post by unutbu on 2008-06-03
Yay! I'm very happy it works for you. :popcorn:

---

### Post by RuleMaker on 2009-04-12
I just wrote this script for myself, for personal use and a little bash practice.
It works, so if you like it you can use it.
```

${execi 500 
cd /tmp
wget -q **http://www.weather.com/outlook/travel/businesstraveler/local/SRXX0006?from=enhsearch_loc** -O weather
farenheit=`cat weather | grep temp= | sed 's/.*temp=\([0-9]\+\).*/\1/;q'`
echo Temperature: $((($farenheit-32)*5/9))C
rm weather}
```

Change the bolded url with your location url on weather.com and add the code to your conkyrc.

(currently it shows for my town - Novi Sad)

Oh, and to not forget to mention odyniec who helped me about the regexp.

---


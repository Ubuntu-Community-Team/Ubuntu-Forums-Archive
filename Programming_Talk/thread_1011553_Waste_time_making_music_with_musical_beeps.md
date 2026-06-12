---
title: "Waste time making music with musical_beeps"
date: 2008-12-14
forum: Programming Talk
---

### Post by mssever on 2008-12-14
The other day, I stumbled across Dr Small's [implementation]("https://wiki.ubuntu.com/drsmall#Scripts") of "[Westminster Quarters]("http://en.wikipedia.org/wiki/Westminster_Quarters")", which uses beep to play hourly chimes via the machine's internal speaker. After running his script, I decided the rhythm was wrong, so I started fooling with the script to set it to how I wanted it. I eventually discovered that his rhythm matched the various recordings I found (I argue that the clocks in said recordings are wrong), but my version was more correct according to music theory.

At any rate, I started to expand Dr Small's script to include the chimes to play on the quarter, half, and three-quarter hours in addition to the top-of-the-hour chime. I use cron to play the chimes. I kept fooling with the script, and eventually ended up with a music library for beep which I'm calling musical_beeps. Virtually none of Dr Small's original script remains.

Since I wasted so much time playing with this, I thought I'd post it here in case someone else has some time to waste. It's got a few peculiarities. For one thing, it's written in Bash instead of a more sensible language. Dr Small's script was in Bash, and since my library grew organically from the original, I had quite a lot invested in it before I realized that I had something separate.

To use musical_beeps, you need several things. First, you need a computer with an internal speaker. In my case, my desktop has one but my laptop doesn't. YMMV. Second, you need the beep package. In Intrepid, beep is installed setuid root, but according to the man page, that isn't the upstream default. So you might need to run your scripts as root (or manually make beep setuid). Finally, you need the library, musical_beeps.sh (documented in comments):
```
#!/bin/bash
# musical_beeps.sh
# By Scott Severance (inspired by Dr Small's implementation of Westminster
# Quarters)
# Debugging switch
#set -x


################################################################################
#                          General Documentation                               #
################################################################################

# musical_beeps is a Bash library to make beep easier to use. It turnes musical
# notation descriptions into beep's arguments. All functions except
# beep_initialize, print_durations, and print_pitches should be called in a
# subshell. Here's a brief example of a C major arpeggio to provide a high-level
# overview of musical_beeps:
# 
# beep_initialize 262 300
# beep $(first_note $C $quarter) $(q_note $E) $(q_note $G) $(dh_note $(up_octave $C))


################################################################################
#                          Function Documentation                              #
################################################################################

# function beep_initialize
# Initialize musical_beeps. Required parameters are the tonic frequency (called
# $C) and the duration of a quarter note specified in milliseconds. Don't call
# this function in a subshell (unless you're doing something exotic).
# 
# You must call this function before calling any other function in musical_beeps
# in order to initialize the notes and durations. You may call this as many
# times as you want. For example, to change the tempo, call this function again
# with the new tempo.
# 
# The first parameter is the tonic frequency in Hertz, which in musical_beeps is
# always called $C. Based on the tonic frequency, variables for the other note
# names are generated, named as in German (German note names are short and
# require no special characters). The natural scale is: $C, $D, $E, $F, $G, $A,
# $H (!!), $C. Sharps are formed by adding -is to the end of the name (e.g., C
# sharp == Cis). Flats are formed by adding -es to the end of the name (e.g., D
# flat == Des). The exceptions are: Es == E flat; As == A flat; and B == B flat
# (English B natural is German H). All notes defined are within a single octave.
# Use the functions up_octave and down_octave as necessary to produce the
# remaining notes.
# 
# The scale is calculated using just (or pure) tuning, as played by fretless
# stringed instruments, woodwinds, brass, voice, etc. It does not use equal
# tuning as found on keyboard instruments and fretted stringed instruments. That
# means that you can't just transpose willy-nilly. Transpose everything to C,
# then set the tonic frequency to the frequency of the pitch you want your scale
# to start from. For your convenience, here's a table of some sample pitches.
# This table shows the frequency of notes using equal tuning and A = 440 Hz.
#
#     +----------+-----------+
#     | Note     | Frequency |
#     +----------+-----------+
#     | C        | 262 Hz    |    Table adapted from:
#     | Cis/Des  | 277 Hz    |    Mugur G. Doroftei, _Music Theory Made Clear_.
#     | D        | 294 Hz    |    Keene, TX, USA: Dorshe Musica, 2000. Page 15.
#     | Dis/Es   | 311 Hz    |
#     | E        | 330 Hz    |
#     | F        | 349 Hz    |
#     | Fis/Ges  | 370 Hz    |
#     | G        | 392 Hz    |
#     | Gis/As   | 415 Hz    |
#     | A        | 440 Hz    |
#     | Ais/B    | 466 Hz    |
#     | H        | 494 Hz    |
#     +----------+-----------+
# 
# The second parameter is the quarter note (crochet) duration in milliseconds.
# Variables for the other notes are generated based on the quarter note. The
# variables are named using American English names: $whole, $half, $quarter,
# $eighth, $sixteenth, $thirty_second, $sixty_fourth. Dotted varieties also
# exist for all durations except $sixty_fourth and $whole. They're named as in
# this example: $dotted_quarter.
# 
# The variables created for both pitches ($C, $D, etc.) and duration are globals,
# so you can reference them from wherever may be necessary. (And because Bash
# doesn't have very good scope rules.)
function beep_initialize {
  local tonic_frequency=$1
  local quarter_note_duration=$2
  
  # Notes
  C=$tonic_frequency
  D=$(_calculate_frequency $C 9 8)      # Interval: Major 2nd
  E=$(_calculate_frequency $C 5 4)      # Interval: Major 3rd
  F=$(_calculate_frequency $C 4 3)      # Interval: Perfect 4th
  G=$(_calculate_frequency $C 3 2)      # Interval: Perfect 5th
  A=$(_calculate_frequency $C 5 3)      # Interval: Major 6th
  H=$(_calculate_frequency $C 15 8)     # Interval: Major 7th
  
  Cis=$(_semitone_up $C $D)
  Dis=$(_semitone_up $D $E)
  #Eis=
  Fis=$(_semitone_up $F $G)
  Gis=$(_semitone_up $G $A)
  Ais=$(_semitone_up $A $H)
  #His=
  
  #Ces=
  Des=$(_semitone_down $D $C)
  Es=$(_semitone_down $E $D)
  #Fes=
  Ges=$(_semitone_down $G $F)
  As=$(_semitone_down $A $G)
  B=$(_semitone_down $H $A)
  
  # Durations
  quarter=$quarter_note_duration
  half=$(_double_time $quarter)
  whole=$(_double_time $half)
  eighth=$(_half_time $quarter)
  sixteenth=$(_half_time $eighth)
  thirty_second=$(_half_time $sixteenth)
  sixty_fourth=$(_half_time $thirty_second)
  dotted_thirty_second=$(tie_notes $thirty_second $sixty_fourth)
  dotted_sixteenth=$(tie_notes $sixteenth $thirty_second)
  dotted_eighth=$(tie_notes $eighth $sixteenth)
  dotted_quarter=$(tie_notes $quarter $eighth)
  dotted_half=$(tie_notes $half $quarter)
}

# Lower a pitch by an octave. Provide a pitch as the argument, and you'll get
# it back an octave lower.
function down_octave {
  local frequency=$1
  echo "scale = 3; $frequency / 2" | bc
}

# Raise a pitch by an octave. Provide a pitch as the argument, and you'll get it
# back an octave higher.
function up_octave {
  local frequency=$1
  echo "scale = 3; $frequency * 2" | bc
}

# Tie two notes by adding two provided durations. Expects two durations as
# arguments and gives back the sum as a single duration. The effect is the same
# as tied notes.
function tie_notes {
  local duration_1=$1
  local duration_2=$2
  echo "$duration_1 + $duration_2" | bc
}

# Create a single duration for a tuple. The arguments are: the total number of
# notes in the tuple; the total duration of the tuple. For example, to create an
# eighth note triplet (3 eighth notes in the time of 2 eighth notes or 1 quarter
# note), you could do something like this:
# 
# triplet=$(tuple 3 $quarter)
# beep $(first_note $C $triplet) $(note $E $triplet) $(note $G $triplet)
function tuple {
  local notes_in_tuple=$1
  local duration_of_tuple=$2
  echo "$duration_of_tuple / $notes_in_tuple" | bc
}

# Generate beep codes for the first note in a tune. This function should be the
# first function called in a beep command, since it doesn't include beep's -n
# argument (which should only separate notes). The first argument is the pitch.
# The second is the duration. The third argument is optional. If specified, it
# adds a rest of the given duration after the note. Normally, it's better to use
# the rest function. This option is mainly provided to enable use of beep's -r
# (repeat) argument.
function first_note {
  local pitch=$1
  local duration=$2
  local following_rest=  # None if third argument not provided
  
  [ $# -eq 3 ] && following_rest=" -D$3"
  echo "-f$pitch -l$duration$following_rest"
}

# Generate beep codes for all notes other than the first. The arguments are the
# same as in first_note. There are shortcut functions (such as q_note) for the
# common durations, so you probably won't use this function very often.
function note {
  local pitch=$1
  local duration=$2

  if [ $# -eq 3 ]; then echo "-n $(first_note $pitch $duration $3)"
  else echo "-n $(first_note $pitch $duration)"
  fi
}

# Generate beep code for a rest. The argument is the duration of the rest. This
# function (though not strictly necessary) is preferred over the third argument
# to note or first_note because it makes for more readable code.
function rest {
  local duration=$1
  echo "-nl0 -D$duration"
}

# Shortcut functions for notes of durations of thirty-second and
# longer. Abbreviations are the first letter of the duration name,
# prefixed by a d if dotted. For example, the function for a half note is h_note,
# and the function for a dotted sixteenth note is ds_note. Each function takes a
# single argument, the note's pitch.

function t_note {
  local pitch=$1
  note $pitch $thirty_second
}

function dt_note {
  local pitch=$1
  note $pitch $dotted_thirty_second
}

function s_note {
  local pitch=$1
  note $pitch $sixteenth
}

function ds_note {
  local pitch=$1
  note $pitch $dotted_sixteenth
}

function e_note {
  local pitch=$1
  note $pitch $eighth
}

function de_note {
  local pitch=$1
  note $pitch $dotted_eighth
}

function q_note {
  local pitch=$1
  note $pitch $quarter
}

function dq_note {
  local pitch=$1
  note $pitch $dotted_quarter
}

function h_note {
  local pitch=$1
  note $pitch $half
}

function dh_note {
  local pitch=$1
  note $pitch $dotted_half
}

function w_note {
  local pitch=$1
  note $pitch $whole
}

# Diagnostic tests

# Print a table listing the current frequency of the notes defined. You don't
# need to call this function in a subshell.
function print_pitches {
  echo -e "Frequency Table (in Hertz)\n=========================="
  echo -e "C\t$C"
  echo -e "Cis\t$Cis"
  echo -e "Des\t$Des"
  echo -e "D\t$D"
  echo -e "Dis\t$Dis"
  echo -e "Es\t$Es"
  echo -e "E\t$E"
  echo -e "F\t$F"
  echo -e "Fis\t$Fis"
  echo -e "Ges\t$Ges"
  echo -e "G\t$G"
  echo -e "Gis\t$Gis"
  echo -e "As\t$As"
  echo -e "A\t$A"
  echo -e "Ais\t$Ais"
  echo -e "B\t$B"
  echo -e "H\t$H"
  [ $(echo "$C == 262" | bc) -eq 0 ] && echo -e "\nIMPORTANT: Since C's frequency is $C Hz, not 262 Hz, the note names should be\nconsidered to merely express a relationship to the tonic, designated C."
}

# Print a table listing the current durations defined. You don't need to call
# this function in a subshell.
function print_durations {
  echo -e "Duration Table (in milliseconds)\n================================"
  echo -e "Sixty-fourth\t\t$sixty_fourth"
  echo -e "Thirty-second\t\t$thirty_second"
  echo -e "Dotted thirty-second\t$dotted_thirty_second"
  echo -e "Sixteenth\t\t$sixteenth"
  echo -e "Dotted sixteenth\t$dotted_sixteenth"
  echo -e "Eighth\t\t\t$eighth"
  echo -e "Dotted eighth\t\t$dotted_eighth"
  echo -e "Quarter\t\t\t$quarter"
  echo -e "Dotted quarter\t\t$dotted_quarter"
  echo -e "Half\t\t\t$half"
  echo -e "Dotted half\t\t$dotted_half"
  echo -e "Whole\t\t\t$whole"
}

################################################################################
#   Helper functions for beep_initialize. Treat them as if they were private.  #
################################################################################


function _calculate_frequency {
  local base=$1
  local numerator=$2
  local denominator=$3
  echo "scale = 3; $base * ($numerator / $denominator)" | bc
}

# Example to help visualize the formula for semitones:
# 
# C                            Cis
# |-----|-----|-----|-----|-----|-----|-----|-----|-----|
#                        Des                            D

function _semitone_up {
  local lower=$1
  local upper=$2
  echo "scale = 3; $lower + ((($upper - $lower) / 9) * 5)" | bc
}

function _semitone_down {
  local upper=$1
  local lower=$2
  echo "scale = 3; $upper - ((($upper - $lower) / 9) * 5)" | bc
}

function _half_time {
  local duration=$1
  echo "$duration / 2" | bc
}

function _double_time {
  local duration=$1
  echo "$duration * 2" | bc
}
```Here are a couple samples of what musical_beeps can do. First, here's my version of "Westminster Quarters": ```
#!/bin/bash
# Westminster Quarters
# 
# There are five sequences which comprise the chimes. The actual chimes
# are permutations of them.

# Debugging switch
#set -x

# Include musical_beeps
builtin cd "$(dirname $0)"  # This makes sourcing musical_beeps independent of the current working directory
. musical_beeps.sh

tonic_frequency=330  # E
quarter_note_duration=700

# Chimes

function chimes_sequence {
  local first_pitch=$1
  local second_pitch=$2
  local third_pitch=$3
  local fourth_pitch=$4
  echo "$(first_note $first_pitch $quarter) $(q_note $second_pitch) $(q_note $third_pitch) $(note $fourth_pitch $(tie_notes $half $eighth)) $(rest $eighth)"
}

function sequence_1 {
  chimes_sequence $E $D $C $lG
}

function sequence_2 {
  chimes_sequence $C $E $D $lG
}

function sequence_3 {
  chimes_sequence $C $D $E $C
}

function sequence_4 {
  chimes_sequence $E $C $D $lG
}

function sequence_5 {
  chimes_sequence $lG $D $E $C
}

function quarter_hour {
  beep $(sequence_1)
}

function half_hour {
  beep $(sequence_2) --new $(sequence_3)
}

function three_quarter_hour {
  beep $(sequence_4) --new $(sequence_5) --new $(sequence_1)
}

function hour {
  local hours=$(date +%l)
  beep $(sequence_2) --new $(sequence_3) --new $(sequence_4) --new $(sequence_5) $(rest $dotted_quarter) $(note $dong $(tie_notes $dotted_half $eighth) $eighth) -r$hours
}

function main {
  local tune=$1

  beep_initialize $tonic_frequency $quarter_note_duration

  # Set up additional notes we need...
  dong=$(down_octave $C)
  lG=$(down_octave $G)  # l for low
  
  case "$tune" in
    first-quarter)
      quarter_hour
      ;;
    second-quarter)
      half_hour
      ;;
    third-quarter)
      three_quarter_hour
      ;;
    full-hour)
      hour
      ;;
    frequency-table)
      print_pitches
      ;;
    *)
      beep -f 1000 -r 2 -n -r 5 -l 10 --new &
      echo -e "Usage: chime_full type\n\nTypes:\n\tfirst-quarter\n\tsecond-quarter\n\tthird-quarter\n\tfull-hour\n\n\tfrequency-table" >&2
      exit 1
      ;;
  esac
}

main "$@"
```Finally, since it's the Christmas season, here's a Christmas song ("The First Noël"):```
#!/bin/bash
# The First Noël, musical_beeps arrangement by Scott Severance
# Tune comes from Wm. Sandy's _Christmas Carols_ (1833), so presumably in the public domain

builtin cd "$(dirname $0)"  # This makes sourcing musical_beeps independent of the current working directory
. musical_beeps.sh

beep_initialize 262 600

hC=$(up_octave $C)

# Measures
# Verse
pickup="$(first_note $E $eighth)  $(e_note $D)"
m0102="$(dq_note $C) $(e_note $D) $(e_note $E) $(e_note $F) $(h_note $G) $(e_note $A) $(e_note $H)"
m0304="$(q_note $hC) $(q_note $H) $(q_note $A) $(h_note $G) $(e_note $A) $(e_note $H)"
m0506="$(q_note $hC) $(q_note $H) $(q_note $A) $(q_note $G) $(q_note $A) $(q_note $H)"
m0708="$(q_note $hC) $(q_note $G) $(q_note $F) $(note $E $(tie_notes $dotted_quarter $sixteenth)) $(rest $sixteenth) $(e_note $E) $(e_note $D)"
m0910="$m0102"
m1112="$m0304"
m1314="$m0506"
m1516="$m0708"
# Refrain
m1718="$(dq_note $C) $(e_note $D) $(e_note $E) $(e_note $F) $(h_note $G) $(e_note $hC) $(e_note $H)"
m1920="$(h_note $A)  $(q_note $A) $(dh_note $G)"
m2122="$(q_note $hC) $(q_note $H) $(q_note $A) $(q_note $G) $(q_note $A) $(q_note $H)"
m2324="$(q_note $hC) $(q_note $G) $(q_note $F) $(dh_note $E)"

# Play song
beep $pickup $m0102 $m0304 $m0506 $m0708 $m0910 $m1112 $m1314 $m1516 $m1718 $m1920 $m2122 $m2324
```

---

### Post by myrtle1908 on 2008-12-14
Haha this is great ...  well done!

---


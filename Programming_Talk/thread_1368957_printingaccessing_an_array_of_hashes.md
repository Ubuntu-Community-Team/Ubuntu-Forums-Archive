---
title: "printing/accessing an array of hashes"
date: 2009-12-31
forum: Programming Talk
---

### Post by gudhead on 2009-12-31
I have a file which is tab delimited(a hit from a DB). I would like to first store say the first and tenth item on each(row) as well as the entire row in a hash. And then build an array of hashes from 2nd,3rd,...... rows respectively. I would then sort each of the rows by score and ID(which are the first and 10th elements of each row) and print the row with the best score. Note: the hits have 2 different ID in column 10. I need to print the best hit based on highest score for each ID.

I have tried to write this code but I really need hints on how to get my best hit/score for each ID:
[SIZE=-1]my @hITS;
while (<CBLAT>) {
    chomp;
    my %row;
    @row{qw( score qID )} = ( split /\t/ )[ 0, 9 ];
    push @hITS, \%row;
}

@hITS = sort {
    $b->{score} <=> $a->{score}
        ||
    $a->{qID} cmp $b->{qID}
} @hITS;

for (@hITS) {
    print "score: $_->{score}  qID: $_->{qID}\n");

}

Once I can access the best hit for each ID based on score, I would also just like to print the corresponding whole row
[/SIZE]

---


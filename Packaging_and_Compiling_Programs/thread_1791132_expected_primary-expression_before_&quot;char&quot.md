---
title: "expected primary-expression before &quot;char&quot;"
date: 2011-06-26
forum: Packaging and Compiling Programs
---

### Post by andereasmehdi on 2011-06-26
hi,
I am new in linux code compiling and i use cygwin.
I ran into *[COLOR=Red]Vocab.cc: In member function `VocabIndex Vocab::metaTagOfType(unsigned int)': Vocab.cc:259: error: expected primary-expression before "char"[/COLOR]*  error. :confused:
Can anyone help me to handle this error?

Here is the Vocab.cc:

```

/*
 * Vocab.cc --
 *    The vocabulary class implementation.
 *
 */

#ifndef lint
static char Copyright[] = "Copyright (c) 1995-2010 SRI International.  All Rights Reserved.";
static char RcsId[] = "@(#)$Header: /home/srilm/devel/lm/src/RCS/Vocab.cc,v 1.43 2010/06/02 05:49:58 stolcke Exp $";
#endif

#ifdef PRE_ISO_CXX
# include <iostream.h>
#else
# include <iostream>
using namespace std;
#endif
#include <string.h>
#include <ctype.h>
#include <assert.h>

#include "C:\cygwin\semanlm\include\srilm\File.h"
#include "C:\cygwin\semanlm\include\srilm\Vocab.h"

#include "C:\cygwin\semanlm\include\srilm\LHash.cc"
#include "C:\cygwin\semanlm\include\srilm\Array.cc"

#ifdef INSTANTIATE_TEMPLATES
INSTANTIATE_LHASH(VocabString,VocabIndex);
INSTANTIATE_ARRAY(VocabString);
#endif

Vocab::Vocab(VocabIndex start, VocabIndex end)
    : byIndex(start), nextIndex(start), maxIndex(end), _metaTag(0)
{
    /*
     * Vocab_None is both the non-index value and the end-token
     * for key sequences used with Tries.  Both need to be
     * the same value so the user or the LM library doesn't have
     * to deal with Map_noKey() and friends.
     */
    assert(Map_noKeyP(Vocab_None));

    /*
     * Make the last Vocab created be the default one used in
     * ostream output
     */
    outputVocab = this;

    /*
     * default is a closed-vocabulary model
     */
    _unkIsWord = false;

    /*
     * do not map word strings to lowercase by defaults
     */
    _toLower = false;

    /*
     * set some special vocabulary tokens to their defaults
     */
    _unkIndex = addWord(Vocab_Unknown);
    _ssIndex = addWord(Vocab_SentStart);
    _seIndex = addWord(Vocab_SentEnd);
    _pauseIndex = addWord(Vocab_Pause);

    /*
     * declare some known non-events
     */
    addNonEvent(_ssIndex);
    addNonEvent(_pauseIndex);
}

// Compute memory usage
void
Vocab::memStats(MemStats &stats) const
{
    stats.total += sizeof(*this) - sizeof(byName) - sizeof(byIndex);
    byName.memStats(stats);
    byIndex.memStats(stats);
}

// map word string to lowercase
// returns a static buffer
static VocabString
mapToLower(VocabString name)
{
    static char lower[maxWordLength + 1];

    unsigned  i;
    for (i = 0; name[i] != 0 && i < maxWordLength; i++) {
    lower[i] = tolower((unsigned char)name[i]);
    }
    lower[i] = '\0';

    assert(i < maxWordLength);

    return lower;
}

// Add word to vocabulary
VocabIndex
Vocab::addWord(VocabString name)
{
    if (_toLower) {
    name = mapToLower(name);
    }

    Boolean found;
    VocabIndex *indexPtr = byName.insert(name, found);

    if (found) {
    return *indexPtr;
    } else {
    if (nextIndex == maxIndex) {
        return Vocab_None;
    } else {
        *indexPtr = nextIndex;
        byIndex[nextIndex] = byName.getInternalKey(name);

        /*
         * Check for metatags, and intern them into our metatag type map
         */
        if (_metaTag != 0) {
        unsigned metaTagLength = strlen(_metaTag);

        if (strncmp(name, _metaTag, metaTagLength) == 0) {
            int type = -1;
            if (name[metaTagLength] == '\0') {
            type = 0;
            } else {
            sscanf(&name[metaTagLength], "%u", &type);
            }
            if (type >= 0) {
            *metaTagMap.insert(nextIndex) = type;
            }
        }
        }

        return nextIndex++;
    }
    } 
}

// add an alternate (alias) name for a word index
VocabIndex
Vocab::addWordAlias(VocabIndex word, VocabString name)
{
    if (_toLower) {
    name = mapToLower(name);
    }

    // make sure word is a valid index
    if (byIndex[word] == 0) {
    return Vocab_None;
    } else {
    // avoid aliasing name to itself
    if (strcmp(name, byIndex[word]) == 0) {
        return word;
    }

    // make sure name isn't otherwise used
    remove(name);

    VocabIndex *indexPtr = byName.insert(name);

    *indexPtr = word;

    return word;
    }
}

// declare word to be a non-event
VocabIndex
Vocab::addNonEvent(VocabIndex word)
{
    /* 
     * First make sure the word is already defined
     */
    if (getWord(word) == 0) {
    return Vocab_None;
    } else {
    *nonEventMap.insert(word) = 1;
    return word;
    }
}

// declare a set of non-events
Boolean
Vocab::addNonEvents(Vocab &nonevents)
{
    VocabIter viter(nonevents);
    Boolean ok = true;

    VocabString name;
    while ((name = viter.next())) {
    if (addNonEvent(name) == Vocab_None) {
        ok = false;
    }
    }

    return ok;
}

// remove word as a non-event
Boolean
Vocab::removeNonEvent(VocabIndex word)
{
    /* 
     * First make sure the word is already defined
     */
    if (getWord(word) == 0) {
    return false;
    } else {
    return nonEventMap.remove(word) != 0;
    }
}

// Get a word's index by its name
VocabIndex
Vocab::getIndex(VocabString name, VocabIndex unkIndex)
{
    if (_toLower) {
    name = mapToLower(name);
    }

    VocabIndex *indexPtr = byName.find(name);

    /*
     * If word is a metatag and not already interned, do it now
     */
    if (indexPtr == 0 &&
    _metaTag != 0 &&
    strncmp(name, _metaTag, strlen(_metaTag)) == 0)
    {
    return addWord(name);
    } else {
    return indexPtr ? *indexPtr : unkIndex;
    }
}

// Get the index of a metatag
VocabIndex
Vocab::metaTagOfType(unsigned type)
{
    if (_metaTag == 0)
    {
    return Vocab_None;
    } 
    else 
    {
    if (type == 0)
    {
        return getIndex(_metaTag);
    } 
    else
    {
        makeArray(char, tagName, strlen(_metaTag) + 20);
        sprintf(tagName, "%s%u", _metaTag, type);
        return getIndex(tagName);
    }
    }
}

// Get a word's name by its index
VocabString
Vocab::getWord(VocabIndex index)
{
    if (index < (VocabIndex)byIndex.base() || index >= nextIndex) {
    return 0;
    } else {
    return (*(Array<VocabString>*)&byIndex)[index];    // discard const
    }
}

// Delete a word by name
void
Vocab::remove(VocabString name)
{
    if (_toLower) {
    name = mapToLower(name);
    }

    VocabIndex *indexPtr = byName.find(name);

    if (indexPtr == 0) {
        return;
    } else if (strcmp(name, byIndex[*indexPtr]) != 0) {
    // name is an alias: only remove the string mapping, not the index
    byName.remove(name);
    } else {
    VocabIndex idx = *indexPtr;

    byName.remove(name);
    byIndex[idx] = 0;
    nonEventMap.remove(idx);
    metaTagMap.remove(idx);

    if (idx == _ssIndex) {
        _ssIndex = Vocab_None;
    }
    if (idx == _seIndex) {
        _seIndex = Vocab_None;
    }
    if (idx == _unkIndex) {
        _unkIndex = Vocab_None;
    }
    if (idx == _pauseIndex) {
        _pauseIndex = Vocab_None;
    }
    }
}

// Delete a word by index
void
Vocab::remove(VocabIndex index)
{
    if (index < (VocabIndex)byIndex.base() || index >= nextIndex) {
    return;
    } else {
    VocabString name = byIndex[index];
    if (name) {
        byName.remove(name);
        byIndex[index] = 0;
        nonEventMap.remove(index);
        metaTagMap.remove(index);

        if (index == _ssIndex) {
        _ssIndex = Vocab_None;
        }
        if (index == _seIndex) {
        _seIndex = Vocab_None;
        }
        if (index == _unkIndex) {
        _unkIndex = Vocab_None;
        }
        if (index == _pauseIndex) {
        _pauseIndex = Vocab_None;
        }
    }
    }
}

// Convert index sequence to string sequence
unsigned int
Vocab::getWords(const VocabIndex *wids, VocabString *words,
                            unsigned int max)
{
    unsigned int i;

    for (i = 0; i < max && wids[i] != Vocab_None; i++) {
    words[i] = getWord(wids[i]);
    }
    if (i < max) {
    words[i] = 0;
    }
    return i;
}

// Convert word sequence to index sequence, adding words if needed
unsigned int
Vocab::addWords(const VocabString *words, VocabIndex *wids, unsigned int max)
{
    unsigned int i;

    for (i = 0; i < max && words[i] != 0; i++) {
    wids[i] = addWord(words[i]);
    }
    if (i < max) {
    wids[i] = Vocab_None;
    }
    return i;
}

// Convert word sequence to index sequence (without adding words)
unsigned int
Vocab::getIndices(const VocabString *words,
          VocabIndex *wids, unsigned int max,
          VocabIndex unkIndex)
{
    unsigned int i;

    for (i = 0; i < max && words[i] != 0; i++) {
    wids[i] = getIndex(words[i], unkIndex);
    }
    if (i < max) {
    wids[i] = Vocab_None;
    }
    return i;
}

// Convert word sequence to index sequence, checking if words are in 
// vocabulary; return false is not, true otherwise.
Boolean
Vocab::checkWords(const VocabString *words, VocabIndex *wids, unsigned int max)
{
    unsigned int i;

    for (i = 0; i < max && words[i] != 0; i++) {
    if ((wids[i] = getIndex(words[i], Vocab_None)) == Vocab_None) {
        return false;
    }
    }
    if (i < max) {
    wids[i] = Vocab_None;
    }
    return true;
}

// parse strings into words and update stats
unsigned int
Vocab::parseWords(char *sentence, VocabString *words, unsigned int max)
{
    char *word;
    unsigned i;

    for (i = 0, word = strtok(sentence, wordSeparators);
     i < max && word != 0;
     i++, word = strtok(0, wordSeparators))
    {
    words[i] = word;
    }
    if (i < max) {
    words[i] = 0;
    }

    return i;
}

/*
 * Length of Ngrams
 */
unsigned int
Vocab::length(const VocabIndex *words)
{
    unsigned int len = 0;

    while (words[len] != Vocab_None) len++;
    return len;
}

unsigned int
Vocab::length(const VocabString *words)
{
    unsigned int len = 0;

    while (words[len] != 0) len++;
    return len;
}

/*
 * Copying (a la strcpy())
 */
VocabIndex *
Vocab::copy(VocabIndex *to, const VocabIndex *from)
{
    unsigned i;
    for (i = 0; from[i] != Vocab_None; i ++) {
    to[i] = from[i];
    }
    to[i] = Vocab_None;

    return to;
}

VocabString *
Vocab::copy(VocabString *to, const VocabString *from)
{
    unsigned i;
    for (i = 0; from[i] != 0; i ++) {
    to[i] = from[i];
    }
    to[i] = 0;

    return to;
}

/*
 * Word containment
 */
Boolean
Vocab::contains(const VocabIndex *words, VocabIndex word)
{
    unsigned i;

    for (i = 0; words[i] != Vocab_None; i++) {
    if (words[i] == word) {
        return true;
    }
    }
    return false;
}

/*
 * Reversal of Ngrams
 */
VocabIndex *
Vocab::reverse(VocabIndex *words)
{
    int i, j;    /* j can get negative ! */

    for (i = 0, j = length(words) - 1;
     i < j;
     i++, j--)
    {
    VocabIndex x = words[i];
    words[i] = words[j];
    words[j] = x;
    }
    return words;
}

VocabString *
Vocab::reverse(VocabString *words)
{
    int i, j;    /* j can get negative ! */

    for (i = 0, j = length(words) - 1;
     i < j;
     i++, j--)
    {
    VocabString x = words[i];
    words[i] = words[j];
    words[j] = x;
    }
    return words;
}

/*
 * Output of Ngrams
 */
Vocab *Vocab::outputVocab;    /* vocabulary implicitly used by operator<< */

void
Vocab::write(File &file, const VocabString *words)
{
    for (unsigned int i = 0; words[i] != 0; i++) {
    fprintf(file, "%s%s", (i > 0 ? " " : ""), words[i]);
    }
}

ostream &
operator<< (ostream &stream, const VocabString *words)
{
    for (unsigned int i = 0; words[i] != 0; i++) {
    stream << (i > 0 ? " " : "") << words[i];
    }
    return stream;
}

ostream &
operator<< (ostream &stream, const VocabIndex *words)
{
    for (unsigned int i = 0; words[i] != Vocab_None; i++) {
    VocabString word = Vocab::outputVocab->getWord(words[i]);

    stream << (i > 0 ? " " : "")
           << (word ? word : "UNKNOWN");
    }
    return stream;
}

/* 
 * Sorting of words and word sequences
 */
Vocab *Vocab::compareVocab;    /* implicit parameter to compare() */

// compare to word indices by their associated word strings
// This should be a non-static member, so we don't have to pass the
// Vocab in a global variable, but then we couldn't use this function
// with qsort() and friends.
// If compareVocab == 0 then comparison by index is performed.
int
Vocab::compare(VocabIndex word1, VocabIndex word2)
{
    if (compareVocab == 0) {
    return word2 - word1;
    } else {
    return strcmp(compareVocab->getWord(word1),
              compareVocab->getWord(word2));
    }
}

int
Vocab::compare(const VocabString *words1, const VocabString *words2)
{
    unsigned int i = 0;

    for (i = 0; ; i++) {
    if (words1[i] == 0) {
        if (words2[i] == 0) {
        return 0;
        } else {
        return -1;    /* words1 is shorter */
        }
    } else {
        if (words2[i] == 0) {
        return 1;    /* words2 is shorted */
        } else {
        int comp = compare(words1[i], words2[i]);
        if (comp != 0) {
            return comp;    /* they differ as pos i */
        }
        }
    }
    }
    /*NOTREACHED*/
}

int
Vocab::compare(const VocabIndex *words1, const VocabIndex *words2)
{
    unsigned int i = 0;

    for (i = 0; ; i++) {
    if (words1[i] == Vocab_None) {
        if (words2[i] == Vocab_None) {
        return 0;
        } else {
        return -1;    /* words1 is shorter */
        }
    } else {
        if (words2[i] == Vocab_None) {
        return 1;    /* words2 is shorted */
        } else {
        int comp = compare(words1[i], words2[i]);
        if (comp != 0) {
            return comp;    /* they differ as pos i */
        }
        }
    }
    }
    /*NOTREACHED*/
}

/*
 * These are convenience methods which set the implicit Vocab used
 * by the comparison functions and returns a pointer to them.
 * Suitable to generate the 'sort' argument used by the iterators.
 */
VocabIndexComparator
Vocab::compareIndex() const
{
    compareVocab = (Vocab *)this;    // discard const
    return &Vocab::compare;
}

VocabIndicesComparator
Vocab::compareIndices() const
{
    compareVocab = (Vocab *)this;    // discard const
    return &Vocab::compare;
}

// Write vocabulary to file
void
Vocab::write(File &file, Boolean sorted) const
{
    VocabIter iter(*this, sorted);
    VocabString word;

    while (!file.error() && (word = iter.next())) {
    fprintf(file, "%s\n", word);
    }
}

// Read vocabulary from file
unsigned int
Vocab::read(File &file)
{
    char *line;
    unsigned int howmany = 0;

    while ((line = file.getline())) {
    /*
     * getline() returns only non-empty lines, so strtok()
     * will find at least one word.  Any further ones on that line
     * are ignored.
     */
    VocabString word = strtok(line, wordSeparators);

    if (addWord(word) == Vocab_None) {
        file.position() << "warning: failed to add " << word
                << " to vocabulary\n";
        continue;
    }
    howmany++;
    }
    return howmany;
}

// Read alias mapping from file
unsigned int
Vocab::readAliases(File &file)
{
    char *line;
    unsigned int howmany = 0;

    while ((line = file.getline())) {
    /*
     * getline() returns only non-empty lines, so strtok()
     * will find at least one word.  Anything after the second word
     * is ignored.
     */
    VocabString alias = strtok(line, wordSeparators);
    VocabString word = strtok(0, wordSeparators);

    if (word == 0) {
        file.position() << "warning: line contains only one token\n";
        continue;
    }

    VocabIndex windex;

    if ((windex = addWord(word)) == Vocab_None) {
        file.position() << "warning: failed to add " << word
                << " to vocabulary\n";
        continue;
    }

    if (addWordAlias(windex, alias) == Vocab_None) {
        file.position() << "warning: failed to add alias " << alias
                << " for word " << word
                << " to vocabulary\n";
        continue;
    }

    howmany++;
    }
    return howmany;
}

VocabIndex
Vocab::highIndex() const
{
    if (nextIndex == 0) {
    return Vocab_None;
    } else {
    return nextIndex - 1;
    }
}

/*
 * Check that vocabulary contains words in the range of ngrams given
 * (used for reading Google ngrams efficiently)
 * startRange == 0 means the beginning (INITIAL) of the sorting order
 * endRange == 0 means the end (FINAL) of the sorting order implicitly
 *
 * Algorithm:
 *    if empty(startRange)
 *        return TRUE
 *    else
 *        if first(startRange) == first(endRange) and 
 *           first(startRange) in vocab
 *        return ngramsInRange(rest(startRange), rest(endRange))
 *        else
 *        if first(startRange) in vocab and
 *           ngramsInRange(rest(startRange), FINAL)
 *            return TRUE
 *        if first(endRange) in vocab and
 *           ngramsInRange(INITIAL, rest(endRange))
 *            return TRUE
 *        for all w in vocab
 *           if w > first(startRange) and w < last(endRange)
 *            return TRUE;
 */
Boolean
Vocab::ngramsInRange(VocabString *startRange, VocabString *endRange)
{
    if ((startRange && startRange[0] == 0) ||
        (endRange && endRange[0] == 0))
    {
    return true;
    } else if (startRange && endRange &&
               strcmp(startRange[0], endRange[0]) == 0 &&
               getIndex(startRange[0]) != Vocab_None)
    {
    return ngramsInRange(&startRange[1], &endRange[1]);
    } else {
        if (startRange && getIndex(startRange[0]) != Vocab_None &&
        ngramsInRange(&startRange[1], 0))
        {
        return true;
    }
    if (endRange && getIndex(endRange[0]) != Vocab_None &&
        ngramsInRange(0, &endRange[1]))
    {
        return true;
    }

        /*
     * Cycle through entire vocabulary, looking for a word that's in range
     */
    VocabIter iter(*this);
    VocabString word;

    while ((word = iter.next())) {
        if ((startRange == 0 || strcmp(startRange[0], word) < 0) &&
            (endRange == 0 || strcmp(word, endRange[0]) < 0))
        {
        return true;
        }
    }
    return false;
    }
}

/*
 * Input/output of word-index mappings
 *    word-index mappings store the VocabString-VocabIndex mapping in
 *    binary data formats.
 *    The format is ascii with one word per line:
 *        index    string
 *    The mapping is terminated by EOF or a line consisting only of ".".
 */
void
Vocab::writeIndexMap(File &file)
{
    // Output index map in order of internal vocab indices.
    // This ensures that vocab strings are assigned indices in the same order
    // on reading, and ensures faster insertions into SArray-based tries.
    for (unsigned i = byIndex.base(); i < nextIndex; i ++) {
    if (byIndex[i]) {
        fprintf(file, "%u %s\n", i, byIndex[i]);
    }
    }
    fprintf(file, ".\n");
}

Boolean
Vocab::readIndexMap(File &file, Array<VocabIndex> &map, Boolean limitVocab)
{
    char *line;

    while ((line = file.getline())) {
    VocabIndex id, newid;

    /*
     * getline() returns only non-empty lines, so strtok()
     * will find at least one word.  Anything after the second word
     * is ignored.
     */
    
    VocabString idstring = strtok(line, wordSeparators);
    VocabString word = strtok(0, wordSeparators);

    if (idstring[0] == '.' && idstring[1] == '\0' && word == 0) {
        // end of vocabulary table
        break;
    }

    if (sscanf(idstring, "%u", &id) != 1 || word == 0) {
        file.position() << "malformed vocab index line\n";
        return false;
    }

    if (limitVocab) {
        newid = getIndex(word);
    } else {
        newid = addWord(word);
    }
    map[id] = newid;
    }

    return true;
}


/*
 * Iteration
 */
VocabIter::VocabIter(const Vocab &vocab, Boolean sorted)
    : myIter(vocab.byName, !sorted ? 0 : (int(*)(const char*,const char*))strcmp)
{
}

void
VocabIter::init()
{
    myIter.init();
}

VocabString
VocabIter::next(VocabIndex &index)
{
    VocabString word;
    VocabIndex *idx;
    if ((idx = myIter.next(word))) {
    index = *idx;
    return word;
    } else {
    return 0;
    }
}

```

And Vocab.h file:
```

/*
 * Vocab.h --
 *    Interface to the Vocab class.
 *
 *
 * SYNOPSIS
 *
 * Vocab represents sets of string tokens as typically used for vocabularies,
 * word class names, etc.  Additionally, Vocab provides a mapping from
 * such string tokens (type VocabString) to integers (type VocabIndex).
 * VocabIndex is typically used to index words in language models to
 * conserve space and speed up comparisons etc.  Thus, Vocab essentially
 * implements a symbol table into which strings can be "interned."
 *
 * INTERFACE
 *
 * VocabIndex(VocabIndex start, VocabIndex end)
 *    Initializes a Vocab and sets the index range.
 *    Indices are allocated starting at start and incremented from there.
 *    No indices are allowed beyond end.
 *    This provides a way to map several distinct Vocabs to disjoint
 *    ranges of integers, and then use them jointly without danger of
 *    confusion.
 *
 * VocabIndex addWord(VocabString token)
 *    Adds a new string to the Vocab, returning the assigned index,
 *    or looks up the index if the token already exists.
 *
 * VocabString getWord(VocabIndex index)
 *    Returns the string token associated with index, or 0 if it none
 *    exists.
 *
 * VocabIndex getIndex(VocabString token)
 *    Returns the index for a string token, or Vocab_None if none exists.
 *
 * void remove(VocabString token)
 * void remove(VocabIndex index)
 *    Deletes an item from the Vocab, either by token or by index.
 *
 * unsigned int numWords()
 *    Returns the number of tokens (and indices) in the Vocab.
 *
 * VocabIndex highIndex()
 *    Returns the highest word index in use, or Vocab_None if 
 *    vocabulary is empty.
 *
 * ITERATION
 *
 * VocabIter implements iterations over Vocabs. 
 *
 * VocabIter(Vocab &vocab)
 *    Creates and initializes an iteration over vocab.
 *
 * void init()
 *    Reset an iteration to the "first" element.
 *
 * VocabString next()
 * VocabString next(VocabIndex &index)
 *    Returns the next Vocab token in an iteration, or 0 if the
 *    iteration is finished.  index is set to the corresponding
 *    index.
 *
 * unsigned int read(File &file)
 *    Read a word list from a file into the Vocab, implicitly performing
 *    an addWord() on each token read.  Returns the number of tokens read.
 *
 * void write(File &file)
 *    Write the current set of word tokes to a file, in random order.
 *
 * NOTE: While an iteration over a Vocab is ongoing, no modifications
 * are allowed to the Vocab, EXCEPT possibly removal of the
 * "current" token/index.
 *
 * An iteration returns the elements of a Vocab in random, but deterministic
 * order. Furthermore, when copied or used in initialization of other objects,
 * VocabIter objects retain the current "position" in an iteration.  This
 * allows nested iterations that enumerate all pairs of distinct elements.
 *
 * Copyright (c) 1995-2010 SRI International.  All Rights Reserved.
 *
 * @(#)$Header: /home/srilm/devel/lm/src/RCS/Vocab.h,v 1.41 2010/06/02 05:49:58 stolcke Exp $
 *
 */

#ifndef _Vocab_h_
#define _Vocab_h_

#ifdef PRE_ISO_CXX
# include <iostream.h>
#else
# include <iostream>
using namespace std;
#endif

#include "C:\cygwin\semanlm\include\srilm\Boolean.h"
#include "C:\cygwin\semanlm\include\srilm\File.h"
#include "C:\cygwin\semanlm\include\srilm\LHash.h"
#include "SArray.h"
#include "Array.h"
#include "C:\cygwin\semanlm\include\srilm\MemStats.h"

#ifdef USE_SHORT_VOCAB
typedef unsigned short    VocabIndex;
#else
typedef unsigned int    VocabIndex;
#endif
typedef const char*    VocabString;

const unsigned int    maxWordLength = 1024;

const VocabIndex    Vocab_None = (VocabIndex)-1;

const VocabString    Vocab_Unknown = "<unk>";
const VocabString    Vocab_SentStart = "<s>";
const VocabString    Vocab_SentEnd = "</s>";
const VocabString    Vocab_Pause = "-pau-";

typedef int (*VocabIndexComparator)(VocabIndex, VocabIndex);
typedef int (*VocabIndicesComparator)(const VocabIndex *, const VocabIndex *);

class Vocab
{
    friend class VocabIter;

public:
    Vocab(VocabIndex start = 0, VocabIndex end = (Vocab_None-1));
    virtual ~Vocab() {};

    virtual VocabIndex addWord(VocabString name);
    virtual VocabIndex addWordAlias(VocabIndex word, VocabString name);
    virtual VocabString getWord(VocabIndex index);
    virtual VocabIndex getIndex(VocabString name,
                    VocabIndex unkIndex = Vocab_None);
    virtual void remove(VocabString name);
    virtual void remove(VocabIndex index);
    virtual unsigned int numWords() const { return byName.numEntries(); };
    virtual VocabIndex highIndex() const;

    /*
     * Special (pseudo-) vocabulary tokens
     */
    virtual VocabIndex &unkIndex() { return _unkIndex; };  /* <unk> index */
    virtual VocabIndex &ssIndex() { return _ssIndex; };       /* <s> index */
    virtual VocabIndex &seIndex() { return _seIndex; };       /* </s> index */
    virtual VocabIndex &pauseIndex() { return _pauseIndex; }; /* -pau- index */

    virtual Boolean &unkIsWord() { return _unkIsWord; };
                    /* consider <unk> a regular word */

    virtual Boolean &toLower() { return _toLower; };
                    /* map word strings to lowercase */

    /*
     * Some Vocab tokens/indices are "pseudo words", i.e., they don't
     * get probabilities since they can only occur in contexts.
     */
    virtual Boolean isNonEvent(VocabString word)    /* pseudo-word? */
    { return isNonEvent(getIndex(word)); };
    virtual Boolean isNonEvent(VocabIndex word) const    /* non-event? */
    { return (!_unkIsWord && (word == _unkIndex)) ||
         nonEventMap.find(word) != 0; };

    virtual VocabIndex addNonEvent(VocabIndex word);
    virtual VocabIndex addNonEvent(VocabString name)
    { return addNonEvent(addWord(name)); };
    virtual Boolean addNonEvents(Vocab &nonevents);
    virtual Boolean removeNonEvent(VocabIndex word);

    /*
     * Handling of meta-count tags: these are tags that represent a token
     * count total, or a type frequency count (count-of-count).
     * If metaTag == "__META__", the following tags acquire special meaning:
     *
     *    __META__        a word count total
     *    __META__1        count of singleton word types
     *    __META__2        count of word types occurring twice
     *    ...            ...
     *    __META__N        count of word types occurring N times
     */
    virtual VocabString &metaTag() { return _metaTag; }; /* meta-count tag */
    Boolean isMetaTag(VocabIndex word)
    { return metaTagMap.find(word) != 0; };
    unsigned typeOfMetaTag(VocabIndex word)
    { unsigned *type = metaTagMap.find(word);
      return type != 0 ? *type : (unsigned)-1; };
    VocabIndex metaTagOfType(unsigned);

    /*
     * Utilities for handling Vocab sequences
     */
    virtual unsigned int getWords(const VocabIndex *wids,
              VocabString *words, unsigned int max);
    virtual unsigned int addWords(const VocabString *words,
              VocabIndex *wids, unsigned int max);
    virtual unsigned int getIndices(const VocabString *words,
                VocabIndex *wids, unsigned int max,
                VocabIndex unkIndex = Vocab_None);
    virtual Boolean checkWords(const VocabString *words,
                   VocabIndex *wids, unsigned int max);
    static unsigned int parseWords(char *line,
                   VocabString *words, unsigned int max);

    static unsigned int length(const VocabIndex *words);
    static unsigned int length(const VocabString *words);
    static VocabIndex *copy(VocabIndex *to, const VocabIndex *from);
    static VocabString *copy(VocabString *to, const VocabString *from);
    static VocabIndex *reverse(VocabIndex *words);
    static Boolean contains(const VocabIndex *words, VocabIndex word);
    static VocabString *reverse(VocabString *words);
    static void write(File &file, const VocabString *words);

    /*
     *  Comparison of Vocabs and their sequences
     */
    static int compare(VocabIndex word1, VocabIndex word2);
                /* order on word indices induced by Vocab */
    static int compare(VocabString word1, VocabString word2)
    { return strcmp(word1, word2); };
    static int compare(const VocabIndex *word1, const VocabIndex *word2);
                /* order on word index sequences */
    static int compare(const VocabString *word1, const VocabString *word2);

    VocabIndexComparator compareIndex() const;
    VocabIndicesComparator compareIndices() const;
    Boolean ngramsInRange(VocabString *startRange, VocabString *endRange);

    /*
     * Miscellaneous
     */
    virtual unsigned int read(File &file);
    virtual unsigned int readAliases(File &file);
    virtual void write(File &file, Boolean sorted = true) const;
    virtual void use() const { outputVocab = (Vocab *)this; }; // discard const

    virtual Boolean readIndexMap(File &file, Array<VocabIndex> &map,
                        Boolean limitVocab = false);
    virtual void writeIndexMap(File &file);

    virtual void memStats(MemStats &stats) const;

    static Vocab *outputVocab;  /* implicit parameter to operator<< */

    static Vocab *compareVocab;    /* implicit parameter to compare() */
protected:
    LHash<VocabString,VocabIndex> byName;
    Array<VocabString> byIndex;
    VocabIndex nextIndex;
    VocabIndex maxIndex;

    LHash<VocabIndex, unsigned> nonEventMap;    /* set of non-event words */
    LHash<VocabIndex, unsigned> metaTagMap;    /* maps metatags to their type:
                           0    count total
                           1    single counts
                           ...
                           N    count of count N */

    // hidden data members (accessed through virtual functions
    VocabIndex _unkIndex;        /* <unk> index */
    VocabIndex _ssIndex;        /* <s> index */
    VocabIndex _seIndex;        /* </s> index */
    VocabIndex _pauseIndex;        /* -pau- index */
    Boolean _unkIsWord;            /* consider <unk> a regular word */
    Boolean _toLower;            /* map word strings to lowercase */
    VocabString _metaTag;        /* meta-count tag */
};

ostream &operator<< (ostream &, const VocabString *words);
ostream &operator<< (ostream &, const VocabIndex *words);

class VocabIter
{
public:
    VocabIter(const Vocab &vocab, Boolean sorted = false);
    void init();
    VocabString next() { VocabIndex index; return next(index); };
    VocabString next(VocabIndex &index);
private:
    LHashIter<VocabString,VocabIndex> myIter;
};

/* 
 * We sometimes use strings over VocabIndex as keys into maps.
 * Define the necessary support functions (see Map.h, LHash.cc, SArray.cc).
 */
static inline unsigned
LHash_hashKey(const VocabIndex *key, unsigned maxBits)
{
    unsigned i = 0;

    /*
     * The rationale here is similar to LHash_hashKey(unsigned),
     * except that we shift more to preserve more of the typical number of
     * bits in a VocabIndex.  The value was optimized to encoding 3 words
     * at a time (trigrams).
     */
    for (; *key != Vocab_None; key ++) {
    i += (i << 12) + *key;
    }
    return LHash_hashKey(i, maxBits);
}

static inline const VocabIndex *
Map_copyKey(const VocabIndex *key)
{
    VocabIndex *copy = new VocabIndex[Vocab::length(key) + 1];
    assert(copy != 0);

    unsigned i;
    for (i = 0; key[i] != Vocab_None; i ++) {
    copy[i] = key[i];
    }
    copy[i] = Vocab_None;

    return copy;
}

static inline void
Map_freeKey(const VocabIndex *key)
{
    delete [] (VocabIndex *)key;
}

static inline Boolean
LHash_equalKey(const VocabIndex *key1, const VocabIndex *key2)
{
    unsigned i;
    for (i = 0; key1[i] != Vocab_None && key2[i] != Vocab_None; i ++) {
    if (key1[i] != key2[i]) {
        return false;
    }
    }
    if (key1[i] == Vocab_None && key2[i] == Vocab_None) {
    return true;
    } else {
    return false;
    }
}
     
static inline int
SArray_compareKey(const VocabIndex *key1, const VocabIndex *key2)
{
    unsigned int i = 0;

    for (i = 0; ; i++) {
    if (key1[i] == Vocab_None) {
        if (key2[i] == Vocab_None) {
        return 0;
        } else {
        return -1;    /* key1 is shorter */
        }
    } else {
        if (key2[i] == Vocab_None) {
        return 1;    /* key2 is shorted */
        } else {
        int comp = SArray_compareKey(key1[i], key2[i]);
        if (comp != 0) {
            return comp;    /* they differ at pos i */
        }
        }
    }
    }
    /*NOTREACHED*/
}

#endif /* _Vocab_h_ */


```

Thanks alot

---

### Post by gmargo on 2011-06-26
Pay attention to the error.
Here's line 259:
```

        makeArray(char, tagName, strlen(_metaTag) + 20);

```You can't pass a type as an argument (or is it a macro?) Did you omit a "sizeof" here?
Is this function from your Array.cc?

---

### Post by andereasmehdi on 2011-06-26
yes you are right but unfortunately this is not my code. i download it from a scientific site with free license: [COLOR=#1F497D][FONT=&quot][/FONT][/COLOR][http://userver.ftw.at/~pucher/semanlm/semanlm0.91.zip]("http://userver.ftw.at/%7Epucher/semanlm/semanlm0.91.zip")
I checked all the files but there is no definition for [COLOR=Red]*makeArray*[/COLOR] [COLOR=Black]I am confused.:confused:
I checked in Array.cc but there is nothing
here is the array.cc:
[/COLOR]```

/*
 * Array.cc --
 *    Extensible array implementation
 *
 */

#ifndef _Array_cc_
#define _Array_cc_

#ifndef lint
static char Array_Copyright[] = "Copyright (c) 1995,1997 SRI International.  All Rights Reserved.";
static char Array_RcsId[] = "@(#)$Header: /home/cvsb2/semanlm/include/srilm/Array.cc,v 1.1 2006/01/12 14:48:17 pucher Exp $";
#endif

#include <assert.h>
#include <stdlib.h>
#include <string.h>

#include "Array.h"

#undef INSTANTIATE_ARRAY
#define INSTANTIATE_ARRAY(DataT) \
    template class Array<DataT>

/*
 * extend the size of an Array to accomodate size elements
 *     Note we want to zero-initialize the data elements by default,
 *    so we call their initializers with argument 0.  This means
 *    that all data type used as arguments to the Array template
 *    need to provide an initializer that accepts 0 as a single argument.
 */
template <class DataT>
void
Array<DataT>::alloc(unsigned int size)
{
    unsigned int newSize = size + 1 + alloc_size/2;
    DataT *newData = new DataT[newSize];
    assert(newData != 0);

#ifdef ZERO_INITIALIZE
    memset(newData, 0, newSize * sizeof(DataT));
#endif

    for (unsigned i = 0; i < alloc_size; i++) {
    newData[i] = _data[i];
    }

    delete [] _data;

    _data = newData;
    alloc_size = newSize;
}

template <class DataT>
void
Array<DataT>::memStats(MemStats &stats) const
{
    stats.total += _size * sizeof(_data[0]);
    stats.wasted += (alloc_size - _size) * sizeof(_data[0]);
}

template <class DataT>
Array<DataT> &
Array<DataT>::operator= (const Array<DataT> &other)
{
    // cerr << "warning: Array::operator= called\n";

    if (&other == this) {
    return *this;
    }

    delete [] _data;

    _base = other._base;
    _size = other._size;
    alloc_size = other.alloc_size;

    _data = new DataT[alloc_size];
    assert(_data != 0);

#ifdef ZERO_INITIALIZE
    memset(_data, 0, alloc_size * sizeof(DataT));
#endif

    for (unsigned i = 0; i < alloc_size; i++) {
    _data[i] = other._data[i];
    }

    return *this;
}

#endif /* _Array_cc_ */


```

---

### Post by gmargo on 2011-06-26
Somehow you are mixing and matching sources.  There is no Vocab.cc in that .zip file.  The Vocab.cc file is present in the SRI download available from [http://www.speech.sri.com/projects/srilm/](http://www.speech.sri.com/projects/srilm/)

"makeArray" is a macro in the **dstruct/src/Array.h** file from the SRI sources.

---

### Post by andereasmehdi on 2011-06-26
hi [COLOR=Black]gamargo. that was so helpful and replacing the file fixes the error. 
I changed the [/COLOR]```
 OBJ_READMATRIX= LHash.o Map.o zio.o Array.o File.o Vocab.o option.o ngram-count.o 
``` and the new ones appears: 
> Vocab.o:Vocab.cc: .text$_ZN5LHashIjjE6removeEjRb[LHash<unsigned int, unsigned int>::remove(unsigned int, bool&)]+0xb): undefined reference to `LHash<unsigned int, unsigned int>::removedData'
Vocab.o:Vocab.cc: ).text$_ZN5LHashIjjE6removeEjRb[LHash<unsigned int, unsigned int>::remove(unsigned int, bool&)]+0x22): undefined reference to `LHash<unsigned int, unsigned int>::removedData'
Vocab.o:Vocab.cc: ).text$_ZN5LHashIjjE6removeEjRb[LHash<unsigned int, unsigned int>::remove(unsigned int, bool&)]+0x106): undefined reference to `LHash<unsigned int, unsigned int>::removedData'
Vocab.o:Vocab.cc: ).text$_ZN5LHashIjjE6removeEjRb[LHash<unsigned int, unsigned int>::remove(unsigned int, bool&)]+0x22b): undefined reference to `LHash<unsigned int, unsigned int>::removedData'I copy the entire LHash.cc and I colorized the important lines for the error:

```

/*
 * LHash.cc --
 *    Linear search hash table implementation
 *
 */

#ifndef _LHash_cc_
#define _LHash_cc_

#ifndef lint
static char LHash_Copyright[] = "Copyright (c) 1995-2010 SRI International.  All Rights Reserved.";
static char LHash_RcsId[] = "@(#)$Header: /home/srilm/devel/dstruct/src/RCS/LHash.cc,v 1.53 2010/06/02 04:52:43 stolcke Exp $";
#endif

#ifdef PRE_ISO_CXX
# include <new.h>
# include <iostream.h>
#else
# include <new>
# include <iostream>
using namespace std;
#endif
#include <stdlib.h>
#include <string.h>
#include <assert.h>

#include "C:\cygwin\semanlm\include\srilm\LHash.h"

#undef INSTANTIATE_LHASH
[COLOR=Red]#define INSTANTIATE_LHASH(KeyT, DataT) \
    template <> DataT *LHash< KeyT, DataT >::removedData = 0; \
    template class LHash< KeyT, DataT >; \
    template class LHashIter< KeyT, DataT >

#ifndef __GNUG__
template <class KeyT, class DataT>
DataT *LHash<KeyT,DataT>::removedData = 0;
#endif /* __GNUG__ */[/COLOR]

#ifdef DEBUG
template <class KeyT, class DataT>
unsigned long LHash<KeyT,DataT>::collisionCount = 0;
#endif

const unsigned minHashBits = 3;        /* minimum no. bits for hashing
                     * tables smaller than this use linear
                     * search to save space */
const float fillRatio = 0.8f;        /* fill ration at which the table is
                     * expanded and rehashed */

#define BODY(b)    ((LHashBody<KeyT,DataT> *)b)

/*
 * Dump the entire hash array to cerr.  Unused slots are printed as "FREE".
 */
template <class KeyT, class DataT>
void
LHash<KeyT,DataT>::dump() const
{
    if (body) {
    unsigned maxEntries = hashSize(BODY(body)->maxBits);
    unsigned i;

    for (i = 0; i < maxEntries; i++) {
        cerr << " " << i << ": ";
        if (Map_noKeyP(BODY(body)->data[i].key)) {
        cerr << "FREE";
        } else {
        cerr << BODY(body)->data[i].key
#ifdef DUMP_VALUES
            /* 
             * Only certain types can be printed.
             */
             << "->" << BODY(body)->data[i].value
#endif /* DUMP_VALUES */
             ;
        }
    }
    } else {
    cerr << "EMPTY";
    }
    cerr << endl;
}

template <class KeyT, class DataT>
void
LHash<KeyT,DataT>::memStats(MemStats &stats) const
{
    stats.total += sizeof(*this);
    if (body) {
        unsigned maxEntries = hashSize(BODY(body)->maxBits);

    stats.total += sizeof(*BODY(body)) +
            sizeof(BODY(body)->data[0]) *
                (maxEntries - 1);
    stats.wasted += sizeof(BODY(body)->data[0]) *
                (maxEntries - BODY(body)->nEntries);
    }
}

/*
 * Compute the actual minimum size required for a given number of entries
 */
static inline unsigned
roundSize(unsigned size)
{
    if (size < hashSize(minHashBits)) {
    return size;
    } else {
    return (unsigned)((size + 1)/ fillRatio);
    }
}

template <class KeyT, class DataT>
void
LHash<KeyT,DataT>::alloc(unsigned size)
{
    unsigned maxBits, maxEntries;
    unsigned i;

    /*
     * round up to power of two
     */
    maxBits = 0;
    while (hashSize(maxBits) < size) {
    assert(maxBits < LHash_maxBitLimit);
    maxBits++;
    }

    maxEntries = hashSize(maxBits);

    //cerr << "LHash::alloc: current " << (body ? BODY(body)->nEntries : 0)
    //     << ", requested " << size 
    //     << ", allocating " << maxEntries << " (" << maxBits << ")\n";

    body = (LHashBody<KeyT,DataT> *)malloc(sizeof(*BODY(body)) +
                   (maxEntries - 1) * sizeof(BODY(body)->data[0]));
    assert(body != 0);

    BODY(body)->maxBits = maxBits;
    BODY(body)->nEntries = 0;

    for (i = 0; i < maxEntries; i++) {
    Map_noKey(BODY(body)->data[i].key);
    }
    //cerr << "memory for header = " <<
    //        ((void *)&(BODY(body)->data[0]) - (void *)BODY(body)) << endl;
    //cerr << "memory per entry = " <<
    //        ((void *)&(BODY(body)->data[3]) - (void *)&(BODY(body)->data[2])) << endl;
}

template <class KeyT, class DataT>
LHash<KeyT,DataT>::LHash(unsigned size)
    : body(0)
{
    if (size != 0) {
    /*
     * determine actual initial size
     */
    alloc(roundSize(size));
    }
}

template <class KeyT, class DataT>
void
LHash<KeyT,DataT>::clear(unsigned size)
{
    if (body) {
    unsigned maxEntries = hashSize(BODY(body)->maxBits);
    unsigned i;

    for (i = 0; i < maxEntries; i++) {
        if (! Map_noKeyP(BODY(body)->data[i].key)) {
        Map_freeKey(BODY(body)->data[i].key);
        }
    }
    free(body);
    body = 0;
    }
    if (size != 0) {
    alloc(roundSize(size));
    }
}

template <class KeyT, class DataT>
void LHash<KeyT,DataT>::setsize(unsigned size)
{
    if (body == 0 && size != 0) {
    alloc(roundSize(size));
    }
}

template <class KeyT, class DataT>
LHash<KeyT,DataT>::~LHash()
{
    clear(0);
}

template <class KeyT, class DataT>
LHash<KeyT,DataT>::LHash(const LHash<KeyT,DataT> &source)
    : body(0)
{
#ifdef DEBUG
    cerr << "warning: LHash copy constructor called\n";
#endif
    *this = source;
}

template <class KeyT, class DataT>
LHash<KeyT,DataT> &
LHash<KeyT,DataT>::operator= (const LHash<KeyT,DataT> &other)
{
#ifdef DEBUG
    cerr << "warning: LHash::operator= called\n";
#endif

    if (&other == this) {
    return *this;
    }

    /*
     * copy hash entries from old to new 
     */
    if (other.body) {
    unsigned maxEntries = hashSize(BODY(other.body)->maxBits);
    /*
     * ensure we have exactly the same size as source table
     */
    clear(0);
    alloc(maxEntries);

    for (unsigned i = 0; i < maxEntries; i++) {
        KeyT thisKey = BODY(other.body)->data[i].key;

        if (!Map_noKeyP(thisKey)) {
        /*
         * Copy key
         */
        BODY(body)->data[i].key = Map_copyKey(thisKey);

        /*
         * Initialize data, required for = operator
         */
        new (&(BODY(body)->data[i].value)) DataT;

        /*
         * Copy data
         */
        BODY(body)->data[i].value = BODY(other.body)->data[i].value;
        }
    }
    BODY(body)->nEntries = BODY(other.body)->nEntries;
    } else {
    clear(0);
    }

    return *this;
}

/*
 * Returns index into data array that has the key which is either
 * equal to key, or indicates the place where key would be placed if it
 * occurred in the array.
 */
template <class KeyT, class DataT>
Boolean
LHash<KeyT,DataT>::locate(KeyT key, unsigned &index) const
{
    assert(!Map_noKeyP(key));

    if (body) {
    unsigned maxBits = BODY(body)->maxBits;
        register MapEntry<KeyT,DataT> *data = BODY(body)->data;

    if (maxBits < minHashBits) {
        /*
         * Do a linear search
         */
        unsigned nEntries = BODY(body)->nEntries;
        register unsigned i;

        for (i = 0; i < nEntries; i++) {
        if (LHash_equalKey(data[i].key, key)) {
            index = i;
            return true;
        }
        }
        index = i;
        return false;
    } else {
        /*
         * Do a hashed search
         */
        unsigned hash = LHash_hashKey(key, maxBits);
        unsigned i;

        for (i = hash; ; i = (i + 1) & hashMask(maxBits))
        {
        if (Map_noKeyP(data[i].key)) {
            index = i;
            return false;
        } else if (LHash_equalKey(data[i].key, key)) {
            index = i;
            return true;
        }
#ifdef DEBUG
        collisionCount += 1;
#endif
        }
    }
    } else {
    return false;
    }
}

template <class KeyT, class DataT>
DataT *
LHash<KeyT,DataT>::find(KeyT key, Boolean &foundP) const
{
    unsigned index;

    if ((foundP = locate(key, index))) {
    return &(BODY(body)->data[index].value);
    } else {
    return 0;
    }
}

template <class KeyT, class DataT>
KeyT
LHash<KeyT,DataT>::getInternalKey(KeyT key, Boolean &foundP) const
{
    unsigned index;
    static KeyT zeroKey;

    if ((foundP = locate(key, index))) {
    return BODY(body)->data[index].key;
    } else {
    return zeroKey;
    }
}

template <class KeyT, class DataT>
DataT *
LHash<KeyT,DataT>::insert(KeyT key, Boolean &foundP)
{
    unsigned index;

    assert(!(Map_noKeyP(key)));

    /*
     * Make sure there is room for at least one entry
     */
    if (body == 0) {
    alloc(1);
    }

    if ((foundP = locate(key, index))) {
    return &(BODY(body)->data[index].value);
    } else {
    unsigned maxEntries = hashSize(BODY(body)->maxBits);
    unsigned nEntries = BODY(body)->nEntries;

    /*
     * Rehash table if necessary
     */
    unsigned minSize = roundSize(nEntries + 1);

    if (minSize > maxEntries) {
        LHashBody<KeyT,DataT> *oldBody = BODY(body);
        unsigned i;

        /*
         * Since LHash_maxEntriesLimit is a power of two minus 1
         * we need to check this only when the array is enlarged
         */
        assert(nEntries < LHash_maxEntriesLimit);

        alloc(minSize);
        BODY(body)->nEntries = nEntries;

        if (BODY(body)->maxBits < minHashBits) {
        /*
         * Just copy old entries to new storage, no reindexing
         * required.
         */
        memcpy(BODY(body)->data, oldBody->data,
            sizeof(oldBody->data[0]) * nEntries);
        } else {
        /*
         * Rehash
         */
        for (i = 0; i < maxEntries; i++) {
            KeyT key = oldBody->data[i].key;

            if (! Map_noKeyP(key)) {
            (void)locate(key, index);
            memcpy(&(BODY(body)->data[index]), &(oldBody->data[i]),
                            sizeof(oldBody->data[0]));
            }
        }
        }
        free(oldBody);

        /*
         * Entries have been moved, so have to re-locate key
         */
        (void)locate(key, index);
    }

    BODY(body)->data[index].key = Map_copyKey(key);

    /*
     * Initialize data to zero, but also call constructors, if any
     */
    memset(&(BODY(body)->data[index].value), 0,
            sizeof(BODY(body)->data[index].value));
    new (&(BODY(body)->data[index].value)) DataT;

    BODY(body)->nEntries++;

    return &(BODY(body)->data[index].value);
    }
}

template <class KeyT, class DataT>
DataT *
LHash<KeyT,DataT>::remove(KeyT key, Boolean &foundP)
{
    unsigned index;

    /*
     * Allocate pseudo-static memory for removed objects (returned by
     * remove()). We cannot make this static because otherwise 
     * the destructor for DataT would be called on it at program exit.
     */
    if (removedData == 0) {
    removedData = (DataT *)malloc(sizeof(DataT));
    assert(removedData != 0);
    }

    if ((foundP = locate(key, index))) {
    Map_freeKey(BODY(body)->data[index].key);
    Map_noKey(BODY(body)->data[index].key);
    memcpy(removedData, &BODY(body)->data[index].value, sizeof(DataT));

    if (BODY(body)->maxBits < minHashBits) {
        /*
         * Linear search mode -- Just move all entries above the
         * the one removed to fill the gap.
         */
        unsigned nEntries = BODY(body)->nEntries;

        memmove(&BODY(body)->data[index],
            &BODY(body)->data[index+1],
            (nEntries - index - 1) * sizeof(BODY(body)->data[0]));
        Map_noKey(BODY(body)->data[nEntries - 1].key);
    } else {
        /*
         * The entry after the one being deleted could actually
         * belong to a prior spot in the table, but was bounced forward due
         * to a collision.   The invariant used in lookup is that
         * all locations between the hash index and the actual index are
         * filled.  Hence we examine all entries between the deleted
         * position and the next free position as whether they need to
         * be moved backward.
         */
        while (1) {
        unsigned newIndex;

        index = (index + 1) & hashMask(BODY(body)->maxBits);

        if (Map_noKeyP(BODY(body)->data[index].key)) {
            break;
        }

        /* 
         * If find returns false that means the deletion has
         * introduced a hole in the table that would prevent
         * us from finding the next entry. Luckily, find 
         * also tells us where the hole is.  We move the 
         * entry to its rightful place and continue filling
         * the hole created by this move.
         */
        if (!locate(BODY(body)->data[index].key, newIndex)) {
            memcpy(&(BODY(body)->data[newIndex]),
               &(BODY(body)->data[index]),
               sizeof(BODY(body)->data[0]));
            Map_noKey(BODY(body)->data[index].key);
        }
        }
    }
    BODY(body)->nEntries--;
    return removedData;
    } else {
    return 0;
    }
}

#ifdef __GNUG__
static
#endif
int (*LHash_thisKeyCompare)();        /* used by LHashIter() to communicate
                     * with compareIndex() */
#ifdef __GNUG__
static
#endif
void *LHash_thisBody;            /* ditto */

template <class KeyT, class DataT>
void
LHashIter<KeyT,DataT>::sortKeys()
{
    /*
     * Store keys away and sort them to the user's orders.
     */
    unsigned maxEntries = hashSize(myLHashBody->maxBits);

    unsigned *sortedIndex = new unsigned[numEntries];
    assert(sortedIndex != 0);

    unsigned i;

    unsigned j = 0;
    for (i = 0; i < maxEntries; i++) {
    if (!Map_noKeyP(myLHashBody->data[i].key)) {
        sortedIndex[j++] = i;
    }
    }
    assert(j == numEntries);

    /*
     * Due to the limitations of the qsort interface we have to 
     * pass extra information to compareIndex in these global
     * variables - yuck. 
     */
    LHash_thisKeyCompare = (int(*)())sortFunction;
    LHash_thisBody = myLHashBody;
    qsort(sortedIndex, numEntries, sizeof(*sortedIndex), compareIndex);

    /*
     * Save the keys for enumeration.  The reason we save the keys,
     * not the indices, is that indices may change during enumeration
     * due to deletions.
     */
    sortedKeys = new KeyT[numEntries];
    assert(sortedKeys != 0);

    for (i = 0; i < numEntries; i++) {
    sortedKeys[i] = myLHashBody->data[sortedIndex[i]].key;
    }

    delete [] sortedIndex;
}

template <class KeyT, class DataT>
LHashIter<KeyT,DataT>::LHashIter(const LHash<KeyT,DataT> &lhash,
                    int (*keyCompare)(KeyT, KeyT))
    : myLHashBody(BODY(lhash.body)), current(0),
      numEntries(lhash.numEntries()), sortFunction(keyCompare)
{
    /*
     * Note: we access the underlying LHash through the body pointer,
     * not the top-level LHash itself.  This allows the top-level object
     * to be moved without affecting an ongoing iteration.
     * XXX: This only works because
     * - it is illegal to insert while iterating
     * - deletions don't cause reallocation of the data
     */
    if (sortFunction && myLHashBody) {
    sortKeys();
    } else {
    sortedKeys = 0;
    }
}

/*
 * This is the callback function passed to qsort for comparing array
 * entries. It is passed the indices into the data array, which are
 * compared according to the user-supplied function applied to the 
 * keys found at those locations.
 */
template <class KeyT, class DataT>
int
LHashIter<KeyT,DataT>::compareIndex(const void *idx1, const void *idx2)
{
    return (*(compFnType)LHash_thisKeyCompare)
            (BODY(LHash_thisBody)->data[*(unsigned *)idx1].key,
             BODY(LHash_thisBody)->data[*(unsigned *)idx2].key);
}

template <class KeyT, class DataT>
LHashIter<KeyT,DataT>::~LHashIter()
{
    delete [] sortedKeys;
}


template <class KeyT, class DataT>
void 
LHashIter<KeyT,DataT>::init()
{
    delete [] sortedKeys;

    current = 0;

    {
    /*
     * XXX: fake LHash object to access numEntries()
     */
    LHash<KeyT,DataT> myLHash(0);

    myLHash.body = myLHashBody;
    numEntries = myLHash.numEntries();
    myLHash.body = 0;
    }

    if (sortFunction && myLHashBody) {
    sortKeys();
    } else {
    sortedKeys = 0;
    }
}

template <class KeyT, class DataT>
DataT *
LHashIter<KeyT,DataT>::next(KeyT &key)
{

    if (myLHashBody == 0) {
    return 0;
    } else {
    unsigned index;

    if (sortedKeys) {
        /*
         * Sorted enumeration -- advance to next key in sorted list
         */
        if (current == numEntries) {
        return 0;
        }

        /*
         * XXX: fake LHash object to access locate()
         */
        LHash<KeyT,DataT> myLHash(0);

        myLHash.body = myLHashBody;
        myLHash.locate(sortedKeys[current++], index);
        myLHash.body = 0;;
    } else {
        /*
         * Detect deletions by comparing old and current number of 
         * entries.
         * A legal deletion can only affect the current entry, so
         * adjust the current position to reflect the next entry was
         * moved.
         */
        if (myLHashBody->nEntries != numEntries) {
        assert(myLHashBody->nEntries == numEntries - 1);

        numEntries --;
        current --;
        }

        /*
         * Random enumeration mode
         */
        unsigned maxBits = myLHashBody->maxBits;

        if (maxBits < minHashBits) {
        /*
         * Linear search mode - advance one to the next entry
         */
        if (current == numEntries) {
            return 0;
        }
        } else {
        unsigned maxEntries = hashSize(maxBits);

        while (current < maxEntries &&
               Map_noKeyP(myLHashBody->data[current].key))
        {
            current++;
        }

        if (current == maxEntries) {
            return 0;
        }
        }

        index = current ++;
    }

    key = myLHashBody->data[index].key;
    return &(myLHashBody->data[index].value);
    }
}

#undef BODY

#endif /* _LHash_cc_ */


```

---

### Post by gmargo on 2011-06-26
If you compare files of the same name in the two source trees, it is obvious that the semanlm code was derived from a much earlier version of the srilm code.

You may have a lot of difficultly combining the two.  Or you might try to download older srilm versions to find the matching one.  Good luck.

---

### Post by andereasmehdi on 2011-06-29
Thanks It works!!

---


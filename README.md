# stream-utils

A set of LINQ-like utilities to easily select chunks of Unix streams without resorting to AWK. 😉

## Installation

Just copy the utilities to `/usr/local/bin` or somewhere on your path.

`cp stream* /usr/local/bin`

## The Utilities

All of the utilities have the same rough interface.  They take one or two parameters:

1. A required numeric argument.
2. An optional filename.  If no filename is given, then reads from `STDIN`.

Example: `cat REALLYBIGFILE | stream-seek 1000 | stream-take 100`

This will seek to the 1000th byte in the stream, then output the next 100 bytes.

All numeric arguments refer to bytes, _not_ to encoded characters!

### stream-seek

Seeks to a position in the input stream.

### stream-take

Takes the specified number of bytes from the current position in the stream and outputs them to `STDOUT`.

### stream-newline

Inserts newlines every _n_ characters.  For example, if you have a really big single-line file (ie. no newlines), then `stream-newline 40` will insert a newline every 40 bytes and output to `STDOUT`.

## Motivation

Reading [really long human genome DNA files](http://uswest.ensembl.org/info/data/ftp/index.html) is a pain. 😁

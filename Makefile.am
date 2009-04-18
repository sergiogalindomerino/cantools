# Make cantools.					-*-Makefile-*-

# Copyright (C) 2007-2009 Andreas Heitmann

# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

## Process this file with automake to produce Makefile.in

AUTOMAKE_OPTIONS= foreign subdir-objects
ACLOCAL_AMFLAGS= -I m4

#	
# What to build and install
#
lib_LTLIBRARIES = libcandbc.la libcanasc.la
bin_PROGRAMS    = dbccopy dbcls asctomat

#
# dbcls
#
dbcls_SOURCES = src/dbcls/dbcls.c
dbcls_LDADD   = libcandbc.la

#
# dbccopy
#
dbccopy_SOURCES = src/dbccopy/dbccopy.c
dbccopy_LDADD   = libcandbc.la

#
# asctomat
#
asctomat_SOURCES = src/asctomat/asctomat.c \
                   src/asctomat/busAssignment.c \
                   src/asctomat/matWrite.c \
                   src/asctomat/messageHash.c \
                   src/asctomat/measurement.c \
                   src/asctomat/signalFormat.c \
                   src/asctomat/measurement.h \
                   src/asctomat/signalFormat.h \
                   src/asctomat/busAssignment.h \
                   src/asctomat/matWrite.h \
                   src/asctomat/messageHash.h \
                   src/hashtable/hashtable.c \
                   src/hashtable/hashtable_itr.c \
                   src/hashtable/hashtable.h \
                   src/hashtable/hashtable_itr.h \
                   src/hashtable/hashtable_private.h

asctomat_LDADD     = libcandbc.la libcanasc.la

# additional include pathes necessary
INCLUDES = -I$(top_srcdir)/src/libcandbc -I$(top_srcdir)/hashtable

DEFS = $(YYDEBUG)

# YACC & LEX: enable -d for debugging
# AM_YFLAGS = -d

## Uncomment to enable debugging of linker script parser
YYDEBUG = -DYYDEBUG=1

#
# library headers, source, etc.
#
include_HEADERS= src/libcandbc/dbcModel.h \
                 src/libcandbc/dbcTypes.h \
                 src/libcandbc/dbcReader.h \
                 src/libcandbc/dbcWriter.h \
                 src/libcanasc/ascReader.h \
                 src/libcanasc/messageDecoder.h

libcandbc_la_SOURCES= \
        src/libcandbc/dbcModel.c \
        src/libcandbc/dbcReader.c \
        src/libcandbc/dbcWriter.c \
        src/libcandbc/parser.y \
        src/libcandbc/lexer.l

libcanasc_la_SOURCES= \
        src/libcanasc/ascReader.c \
        src/libcanasc/messageDecoder.c

libcandbc_la_CPPFLAGS= -I$(top_builddir)/src/libcandbc
libcandbc_la_LDFLAGS= -version-info 0:2:0

libcanasc_la_CPPFLAGS= -I$(top_builddir)/src/libcanasc
libcanasc_la_LDFLAGS= -version-info 0:2:0
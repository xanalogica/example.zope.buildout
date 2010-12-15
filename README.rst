=======================
 example.zope.buildout
=======================

This is a example buildout for running a Zope webserver of version 2.12 (when
it was eggified) or later.  It is designed as a starting point and to be easy
to modify according to your needs.

You may reuse any part of this buildout however you see fit.  It is intended
to be borrowed from.


Installation
============

The following sequence of commands will set up a basic webserver::

 $ git clone git://github.com/xanalogica/example.zope.buildout.git  yourproject
 $ cd yourproject
 $ cp etc/example.cfg buildout.cfg
 $ python bootstrap.py
 $ bin/buildout

Review the files *buildout.cfg* and *etc/base.cfg* for aspects that are
configurable.  Your site can now be brought up using::

 $ bin/devinstance fg
 $ firefox http://localhost:8080
 (log in as user 'admin', password 'admin')


Finding Your Way Around
=======================

bin/
    Various executable commands are placed in by buildout recipes and any eggs
    that you install.

    The **bin/develop** command comes from the *mr.developer* buildout-recipe
    for managing your Git/Subversion checkouts and is used by you often.

    The **bin/test** command is for running your unit tests.

    The **bin/devinstance** and **bin/instance** commands are for bringing up
    the Zope webserver, in development or production mode respectively.

etc/
    Contains reference files included by your buildout.cfg file.

logs/
    Receives all logfiles produced by the Zope/ZEO server(s).

othereggs/
    A place to temporarily place eggs needed in a buildout that you have not
    yet published or that have been patched and the patch is still pending
    upstream.  Not used very often.

parts/
    Automatically managed by *zc.buildout*, this directory contains a
    subdirectory for each part making up your buildout.  One of the most
    important ones is **parts/allsource/** which contains a representation of all
    of the source code that makes up your Zope webserver, both the official
    Zope releases and your customized source.  It combines egg namespaces into
    one directory hierarchy and is very useful for searching the source in a
    coherent fashion.

var/
    Contains the *Data.fs* storage file for the ZODB (Zope Object Database).
    Be sure to back up this file for safekeeping but otherwise there is
    nothing under var/ that requires manual adjustment.

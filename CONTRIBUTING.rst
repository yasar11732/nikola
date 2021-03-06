Patch submission guidelines [1]_
--------------------------------

Here are some guidelines about how you can contribute to Nikola:

* First, make sure there is an open issue for your change. Perhaps,
  if it's a new feature, you probably want to
  `discuss it first <http://groups.google.com/group/nikola-discuss>`_

* **Create a new Git branch specific to your change(s).** For example, if
  you're adding a new feature to foo the bars, do something like the
  following::

    $ git checkout master
    $ git pull
    $ git checkout -b foo-the-bars
    <hack hack hack>
    $ git push origin HEAD
    <submit pull request based on your new 'foo-the-bars' branch>

  This makes life much easier for maintainers if you have (or ever plan to
  have) additional changes in your own ``master`` branch.

.. admonition:: A corollary: 

      Please **don't put multiple fixes/features in the same
      branch/pull request**! In other words, if you're hacking on new feature X
      and find a bugfix that doesn't *require* new feature X, **make a new
      distinct branch and PR** for the bugfix.
      
* While working, **rebase instead of merging** (if possible).  We encourage
  using ``git rebase`` instead of ``git merge``.  If you are using
  ``git pull``, please run ``git config pull.rebase true`` to prevent merges
  from happening and replace them with rebase goodness.  There is also an
  “emergency switch” in case rebases fail and you do not know what to do:
  ``git pull --no-rebase``.
* **Make sure documentation is updated** -- at the very least, keep docstrings
  current, and if necessary, update the ReST documentation in ``docs/``.
* **Add a changelog entry** at the top of ``CHANGES.txt`` mentioning issue number
  and in the correct Features/Bugfixes section.
* **Run flake8** for style consistency. Use ``flake8 --ignore=E501 .``
* **Try writing some tests** if possible -- again, following existing tests is
  often easiest, and a good way to tell whether the feature you're modifying is
  easily testable.
* Make sure to mention the issue it affects in the description of your pull request,
  so it's clear what to test and how to do it.
* There are some quirks to how Nikola's codebase is structured, and to how
  some things need to be done [2]_ but don't worry, we'll guide you!
  
.. [1] Very inspired by `fabric's <https://github.com/fabric/fabric/blob/master/CONTRIBUTING.rst>`_ thanks!

.. [2] For example, logging, or always making sure directories are created using ``utils.makedirs()``

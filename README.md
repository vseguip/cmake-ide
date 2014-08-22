cmake-json
==========

Emacs package to call CMake to find out include paths and other compiler flags so that
autocompletion and on-the-fly syntax checking work. Depends on
[flycheck](https://github.com/flycheck/flycheck) and
[auto-complete-clang](https://github.com/brianjcj/auto-complete-clang).
Support might be added for other packages later.

Usage
-----

Add this to your `.emacs` / `init.el`:

    (add-hook 'c-mode-common-hook (lambda ()
                                    (add-hook 'find-file-hook (lambda ()
                                                                (cmake-json-run buffer-file-name)))))

If `ac-clang-flags-c` or `ac-clang-flags-c++` are set, they will be added to `ac-clang-flags`.
These variables should be set. Particularly, they should contain the system include paths.
And... that's it. It works by calling cmake and parsing the resulting JSON file with compiler flags.
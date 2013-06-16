ansible-stuff
=============

My ansible-stuff repository

Look on http://ansible.cc and http://github.com/ansible/ansible for
the real stuff

update_alternatives
-------------------

Handle debian `update-alternatives` in a idempotent way. Maintain symbolic links determining default commands. Can ensure that the highest priority alternative is choosen or select a specific binary as the choosen one

<table>
<tr>
<th class="head">parameter</th>
<th class="head">required</th>
<th class="head">default</th>
<th class="head">choices</th>
<th class="head">comments</th>
</tr>
<tr>
<td>link</td>
<td>yes</td>
<td></td>
<td><ul></ul></td>
<td>Name of the link group (e.g. editor, awk). To list aviable link groups use update-alternatives --get-selections</td>
</tr>
<tr>
<td>target</td>
<td>yes</td>
<td></td>
<td><ul><li>file</li><li>best</li></ul></td>
<td>To which absolute path link should point, updates link group as well, must start with a "/", or if set to "best" the linkgroup with the highest priority is used</td>
</tr>
</table>

* This verifies that editor points to /usr/bin/vim.basic (if /usr/bin/vim.basic is a valid alternative)

```
update_alternatives link=editor target=/usr/bin/vim.basic
```
* Point to the highest priority installed alternatives

```
update_alternatives link=editor target=best
```


#### Notes
This applies to Debian and Ubuntu systems only!

#### Installation
Copy update_alternatives over to your ANSIBLE_LIBRARY directory.


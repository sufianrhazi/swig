# Variable Filters

Used to modify variables. Filters are added directly after variable names, separated by the pipe (|) character. You can chain multiple filters together, applying one after the other in succession.

## Example

    {{ name|title }} was born on {{ birthday|date('F jS, Y') }} and has {{ bikes|length|default("zero") }} bikes.

## Built-In Filters

### add(value)

Adds the value to the variable. Strings that can be converted to integers will be summed, not concatenated, as in the example below.

#### Arguments

1. <var>**value**</var> (_mixed_) The value to add to the variable before printing it to the page. Accepts any `array`, `object`, `number`, and `string`.

### addslashes

Returns a string with backslashes in front of characters that need to be quoted for database queries, etc.

* single quote `'`
* double quote `"`
* backslash `\`

### capitalize

Capitalize the first character in the string.

### date(format)

Convert a valid date into a format as specified. Mostly conforms to [php.net's date formatting](http://php.net/date).

#### Arguments

1. <var>**format**</var> (_string_) The format to convert the date to.

<table style="width: 100%">
    <caption>Date formatting character information from <a href="http://php.net/date">php.net/date</a>.</caption>
    <thead>
        <tr>
            <th>Format Character</th>
            <th>Description</th>
            <th>Example Output</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="col" colspan="3">Day</th>
        </tr>
        <tr>
            <th scope="row"><code>d</code></th>
            <td>Day of the month, 2 digits with leading zeros</td>
            <td><samp>01</samp> - <samp>31</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>D</code></th>
            <td>A textual representation of a day, three letters</td>
            <td><samp>Mon</samp> - <samp>Sun</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>j</code></th>
            <td>Day of the month without leading zeros</td>
            <td><samp>1</samp> - <samp>31</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>l</code></th>
            <td>A full textual representation of the day of the week</td>
            <td><samp>Monday</samp> - <samp>Sunday</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>N</code></th>
            <td>ISO-8601 numeric representation of the day of the week</td>
            <td><samp>1</samp> - <samp>7</samp> (Monday - Sunday)</td>
        </tr>
        <tr>
            <th scope="row"><code>S</code></th>
            <td>English ordinal suffix for the day of the month, 2 characters</td>
            <td><samp>st</samp>, <samp>nd</samp>, <samp>rd</samp>, or <samp>th</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>w</code></th>
            <td>Numeric representation of the day of the week</td>
            <td><samp>0</samp> - <samp>6</samp> (Sunday - Saturday)</td>
        </tr>
        <tr>
            <th scope="col" colspan="3">Month</th>
        </tr>
        <tr>
            <th scope="row"><code>F</code></th>
            <td>A full textual representation of a month, such as January or March</td>
            <td><samp>January</samp> - <samp>December</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>m</code></th>
            <td>Numeric representation of a month, with leading zeros</td>
            <td><samp>12</samp> - <samp>01</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>M</code></th>
            <td>A short textual representation of a month, three letters</td>
            <td><samp>Jan</samp> - <samp>Dec</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>n</code></th>
            <td>Numeric representation of a month, without leading zeros</td>
            <td><samp>1</samp> - <samp>12</samp></td>
        </tr>
        <tr>
            <th scope="col" colspan="3">Year</th>
        </tr>
        <tr>
            <th scope="row"><code>Y</code></th>
            <td>A full numeric representation of a year, 4 digits</td>
            <td><samp>1999</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>y</code></th>
            <td>A two digit representation of a year</td>
            <td><samp>99</samp></td>
        </tr>
        <tr>
            <th scope="col" colspan="3">Time</th>
        </tr>
        <tr>
            <th scope="row"><code>a</code></th>
            <td>Lowercase Ante meridiem and Post meridiem</td>
            <td><samp>am</samp> or <samp>pm</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>A</code></th>
            <td>Uppercase Ante meridiem and Post meridiem</td>
            <td><samp>AM</samp> or <samp>PM</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>g</code></th>
            <td>12-hour format of an hour without leading zeros</td>
            <td><samp>1</samp> - <samp>12</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>G</code></th>
            <td>24-hour format of an hour without leading zeros</td>
            <td><samp>0</samp> - <samp>23</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>h</code></th>
            <td>12-hour format of an hour with leading zeros</td>
            <td><samp>01</samp> - <samp>12</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>H</code></th>
            <td>24-hour format of an hour with leading zeros</td>
            <td><samp>00</samp> - <samp>23</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>i</code></th>
            <td>Minutes with leading zeros</td>
            <td><samp>00</samp> - <samp>59</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>s</code></th>
            <td>Seconds, with leading zeros</td>
            <td><samp>00</samp> - <samp>59</samp></td>
        </tr>
        <tr>
            <th scope="col" colspan="3">Timezone</th>
        </tr>
        <tr>
            <th scope="row"><code>O</code></th>
            <td>Difference to Greenwich time (GMT) in hours</td>
            <td><samp>+0200</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>Z</code></th>
            <td>Timezone offset in seconds. The offset for timezones west of UTC is always negative, and for those east of UTC is always positive.</td>
            <td><samp>-43200</samp> - <samp>50400</samp></td>
        </tr>
        <tr>
            <th scope="col" colspan="3">Full Date &amp; Time</th>
        </tr>
        <tr>
            <th scope="row"><code>r</code></th>
            <td><a href="http://www.faqs.org/rfcs/rfc2822">RFC 2822</a> formatted date</td>
            <td><samp>Sat, 10 Sep 2011 14:34:30 -0700</samp></td>
        </tr>
        <tr>
            <th scope="row"><code>U</code></th>
            <td>Seconds since the Unix Epoch (January 1 1970 00:00:00 GMT)</td>
            <td><samp>1315690513</samp></td>
        </tr>
    </tbody>
</table>

### default(value)

If the variable is `undefined`, `null`, or `false`, a default return value can be specified.

#### Arguments

1. <var>**value**</var> (_mixed_) Fallback value if the variable is falsy.

### escape([type]) / e([type])

Force escape the output of the variable. Optionally use `e` as a shortcut filter name.

#### Arguments

1. <var>**type**</var> (_string_) _optional_ passing "js" as the type will force JavaScript-safe escaping.

### first

Returns the first element of an array. Uses [underscore.js first](http://documentcloud.github.com/underscore/#first)

### join(glue)

If the value is an Array, you can join each value with a delimiter and return it as a string.

#### Arguments

1. <var>**glue**</var> (_string_) Concatenation string to join each item in the array with.

### json_encode

Return a JSON string of the variable.

### last

Returns the last element of an array. Uses [underscore.js last](http://documentcloud.github.com/underscore/#last)

### length

Return the `length` property of the value.

### lower

Return the variable in all lowercase letters.

### raw

Do not escape the output of the variable.

### replace(search, replace[, flags])

Uses built-in JavaScript replace method. Provide a regular-expression or a string and a replacement string.

#### Arguments

1. <var>**search**</var> (_string_) string converted to a regular expression. Example: `'\s'` will become `/\s/`, while `'s'` will become `/s/`
2. <var>**replace**</var> (_string_) a string to replace the matched parts from <var>search</var>
3. <var>**flags**</var> (_string_) _optional_ Regular expression flags. [[reference]](https://developer.mozilla.org/en/JavaScript/Guide/Regular_Expressions#Advanced_Searching_With_Flags)

### reverse

If the value is an Array, this filter will reverse all items in the array.

### striptags

Strip all HTML/XML tags.

### title

Change the output to title case–the first letter of every word will uppercase, while all the rest will be lowercase.

### uniq

Produces a duplicate-free version of the array. Uses [underscore.js uniq](http://documentcloud.github.com/underscore/#uniq)

### upper

Return the variable in all uppercase letters

### url_encode

Encode a URI component.

### url_decode

Decode a URI component.

## Writing Custom Filters

Custom filters are very easy to write for your own project that uses Swig.

Create a file called `myfilters.js` and include it in the Swig init function:

    swig.init({ filters: require('myfilters') });

In your `myfilters.js` file, each filter method is just a simple javascript method. For example, here's a filter to make a variable all lowercase:

    exports.lower = function (input) {
        return input.toString().toLowerCase();
    };

For more examples, view the [filters.js source file](../lib/filters.js)
# get-plugin-name
Copy this code to console in this URL 'wp-admin/update-core.php'

```
const plugins = jQuery('.plugins').find('.plugin-title');
const pluginList = [];
jQuery.each(plugins, function(index, plugin) {
    let pluginTitle = jQuery(plugin).html().trim();

    // Extract the plugin name, current version, and new version
    const nameMatch = pluginTitle.match(/<strong>(.*?)<\/strong>/);
    const currentVersionMatch = pluginTitle.match(/You have version ([\d.]+) installed/);
    const newVersionMatch = pluginTitle.match(/Update to ([\d.]+)/);

    if (nameMatch && currentVersionMatch && newVersionMatch) {
        const pluginName = nameMatch[1];
        const currentVersion = currentVersionMatch[1];
        const newVersion = newVersionMatch[1];

        // Format the result
        const formattedResult = `${pluginName} | ${currentVersion} -> ${newVersion}`;
        pluginList.push(formattedResult);
    }
});

// Log the entire list in one console log
console.log(pluginList.map((plugin, index) => `- ${plugin}`).join('\n'));
```

# Spreadsheet Version

```
const domain = window.location.origin;

const today = new Date();
const formattedDate = today.toLocaleDateString('en-US', {
    year: 'numeric',
    month: 'long',
    day: 'numeric'
});

const plugins = jQuery('.plugins').find('.plugin-title');
const pluginList = [];
jQuery.each(plugins, function(index, plugin) {
    let pluginTitle = jQuery(plugin).html().trim();
    
    // Extract the plugin name, current version, and new version
    const nameMatch = pluginTitle.match(/<strong>(.*?)<\/strong>/);
    const currentVersionMatch = pluginTitle.match(/You have version ([\d.]+) installed/);
    const newVersionMatch = pluginTitle.match(/Update to ([\d.]+)/);

    if (nameMatch && currentVersionMatch && newVersionMatch) {
        const pluginName = nameMatch[1];
        const currentVersion = currentVersionMatch[1];
        const newVersion = newVersionMatch[1];
        
        // Format the result
        const formattedResult = `${formattedDate}\t${domain}\t${pluginName}\t${currentVersion} \t${newVersion}`;
        pluginList.push(formattedResult);
    }
});

// Log the entire list in one console log
console.log(pluginList.join('\n'));
```

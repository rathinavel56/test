https://www.c-sharpcorner.com/article/asp-net-mvc5-kendo-ui-how-to-work-with-editors-and-customize-it/

http://dojo.telerik.com/@ggkrustev/ucaD

https://github.com/AbhishekGhosh/Kendo-Web-UI/tree/master/js

https://github.com/toddmotto/kendo-html-editor/blob/master/index.html

http://dojo.telerik.com/AnEbe


<script src="http://code.jquery.com/jquery-1.12.4.min.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js"></script>
<script src="http://kendo.cdn.telerik.com/2016.3.914/js/kendo.all.min.js"></script>


<!DOCTYPE html>
<html>
<head>
    <base href="http://demos.telerik.com/kendo-ui/editor/custom-tools">
    <style>html { font-size: 14px; font-family: Arial, Helvetica, sans-serif; }</style>
    <title></title>
    <link rel="stylesheet" href="//kendo.cdn.telerik.com/2016.3.1028/styles/kendo.common.min.css" />
    <link rel="stylesheet" href="//kendo.cdn.telerik.com/2016.3.1028/styles/kendo.blueopal.min.css" />
    <link rel="stylesheet" href="//kendo.cdn.telerik.com/2016.3.1028/styles/kendo.blueopal.mobile.min.css" />

    <script src="//kendo.cdn.telerik.com/2016.3.1028/js/jquery.min.js"></script>
    <script src="//kendo.cdn.telerik.com/2016.3.1028/js/kendo.all.min.js"></script>
</head>
<body>
<div id="example">
    <div class="box wide">
        <h4>Information</h4>
        <p>
            The following demo shows how to customize some of the native Editor tools (font size, font name and block format) by modifying the tools' item
            collections, as well as how to create completely custom tools.
        </p>
    </div>

    <textarea id="editor" rows="10" cols="30" style="width:100%;height:400px">
            &lt;p&gt;&lt;img src=&quot;../content/web/editor/kendo-ui-web.png&quot; alt=&quot;Editor for ASP.NET MVC logo&quot; style=&quot;display:block;margin-left:auto;margin-right:auto;&quot; /&gt;&lt;/p&gt;
            &lt;p&gt;
                Kendo UI Editor allows your users to edit HTML in a familiar, user-friendly way.&lt;br /&gt;
                In this version, the Editor provides the core HTML editing engine, which includes basic text formatting, hyperlinks, lists,
                and image handling. The widget &lt;strong&gt;outputs identical HTML&lt;/strong&gt; across all major browsers, follows
                accessibility standards and provides API for content manipulation.
            &lt;/p&gt;
            &lt;p&gt;Features include:&lt;/p&gt;
            &lt;ul&gt;
                &lt;li&gt;Text formatting &amp; alignment&lt;/li&gt;
                &lt;li&gt;Bulleted and numbered lists&lt;/li&gt;
                &lt;li&gt;Hyperlink and image dialogs&lt;/li&gt;
                &lt;li&gt;Cross-browser support&lt;/li&gt;
                &lt;li&gt;Identical HTML output across browsers&lt;/li&gt;
                &lt;li&gt;Gracefully degrades to a &lt;code&gt;textarea&lt;/code&gt; when JavaScript is turned off&lt;/li&gt;
            &lt;/ul&gt;
            &lt;p&gt;
                Read &lt;a href=&quot;http://docs.telerik.com/kendo-ui&quot;&gt;more details&lt;/a&gt; or send us your
                &lt;a href=&quot;http://www.telerik.com/forums/&quot;&gt;feedback&lt;/a&gt;!
            &lt;/p&gt;
    </textarea>

    <script type="text/x-kendo-template" id="backgroundColor-template">
        <label for='templateTool' style='vertical-align:middle;'>Background:</label>
        <select id='templateTool' style='width:90px'><option value=''>none</option><option value='\#ff9'>yellow</option><option value='\#dfd'>green</option></select>
    </script>

    <script>
        $("#editor").kendoEditor({
            tools: [
                {
                    name: "fontName",
                    items: [].concat(
                        kendo.ui.Editor.prototype.options.fontName[8],
                        [{ text: "Garamond", value: "Garamond, serif" }]
                    )
                },
                {
                    name: "fontSize",
                    items: [].concat(
                        kendo.ui.Editor.prototype.options.fontSize[0],
                        [{ text: "16px", value: "16px" }]
                    )
                },
                {
                    name: "formatting",
                    items: [].concat(
                        kendo.ui.editor.FormattingTool.prototype.options.items[0],
                        [{ text: "Fieldset", value: "fieldset" }]
                    )
                },
                {
                    name: "customTemplate",
                    template: $("#backgroundColor-template").html()
                },
                {
                    name: "custom",
                    tooltip: "Insert a horizontal rule",
                    exec: function(e) {
                        var editor = $(this).data("kendoEditor");
                        editor.exec("inserthtml", { value: "<hr />" });
                        editor.refresh();
                    }
                }
            ]
        });

        $("#templateTool").kendoDropDownList({
            change: function(e) {
                $("#editor").data("kendoEditor").body.style.backgroundColor = e.sender.value();
            }
        });

    </script>

</div>


</body>
</html>

**What It Is**

A template for new projects in Visual Studio 2017 and Visual Studio 2019 that creates an HTML application with TypeScript that can use React and other Node modules.

The project contains an HTML file, a CSS file and a TypeScript file with some basic sample code.  The TypeScript file can contain React code.

**What It Does**

When started with F5 a project created with this template will start a web server, IIS Express, and show a ticking time in the selected web browser.  The code to show the time is in a TypeScript class.

**Debugging in Visual Studio**

This template is very similar to the [HTML Application with TypeScript template](https://marketplace.visualstudio.com/items?itemName=Rich-Newman.TypeScriptHTMLApplicationTemplate).  As in that template, this template allows debugging from Visual Studio in Chrome, Edge and Internet Explorer. Just create a project with the template, wait for the Node modules to auto-install, set a breakpoint in Visual Studio, and hit F5. There is no need to use the browser development tools. This makes the template useful as an HTML plus TypeScript playground.

**Node Modules and Webpack**

The key difference to the HTML Application with TypeScript template is that this template is set up to use React installed as a Node module.  For this it uses a module bundler, Webpack.  Set-up for this kind of project in an IDE like Visual Studio can be difficult.  A motivation for this template was to create something that will do it for you with a minimal configuration.

You can use other third-party node modules than React if necessary.  Just add them to package.json under 'dependencies', and install them (rightclick package.json in Solution Explorer/Restore Packages).  Now you should be able to import them in your codefiles. 

**Type Definition Files, @types** 

For TypeScript to recognize the types in an installed third-party node module you may also need to [install type definition files](https://www.typescriptlang.org/docs/handbook/2/type-declarations.html#definitelytyped--types), which you can do in the same way as above.  If you look in package.json you can see react and react-dom are listed under dependencies, and @types/react and @types/react-dom are listed under devDependencies.  The @types packages contain the type definition files, and mean that TypeScript doesn't show errors in Visual Studio when using React keywords.

**Where the Template Appears**

In Visual Studio 2017 this template will appear under 'TypeScript' under 'Other Languages' in the New Project dialog.  This needs the correct dependencies installed, see below. In Visual Studio 2019's 'Create a new project' dialog the easiest way to find it is to filter by Language = TypeScript. In both cases it appears as 'HTML Application with TypeScript and React'.

Please be aware that *this template is based on ASP<span>.</span>NET*, so you will need the ASP<span>.</span>NET workload installed in Visual Studio 2017 or Visual Studio 2019.  If the workload is not there the template will not appear.  It does not need Node.js development or .Net desktop development workloads.

**Possible Warning Message**

Note that when using this template you may get a warning message similar to 'Your project is built using TypeScript 4.1, but the TypeScript language service version currently in use by Visual Studio is 4.2.'   

This can happen if the project template is using a more recent version of TypeScript than Visual Studio has access to.  However, in that case as far as I can work out both the build and the language service will use the later version, so there is no problem.

The error message can be suppressed by giving Visual Studio access to the later version of TypeScript.  At the time of writing the template is using TypeScript 4.2 which can be [installed into Visual Studio from Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-42).

**Adding More Code Files**

One advantage of using a module bundler is that we can use [TypeScript modules](https://www.typescriptlang.org/docs/handbook/modules.html) without the need for any additional set-up.  That is, we can add a new .ts or .tsx file to the project, write code in it and then export the parts we want to use elsewhere in the project, as [shown in the TypeScript documentation](https://www.typescriptlang.org/docs/handbook/modules.html#export).  We can then [import](https://www.typescriptlang.org/docs/handbook/modules.html#import) into our existing code where we want the new code to be used.  When we build Webpack will deal with linking the code files together and creating one combined JavaScript file that works.
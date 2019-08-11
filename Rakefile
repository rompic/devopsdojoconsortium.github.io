require "html-proofer" # Require gem for using within tasks

task :default do
  puts "Running CI tasks..."
  sh("JEKYLL_ENV=production bundle exec jekyll build --destination _site")
  # Add HTMLProofer.check_directory("./_site").run in order to start checking
  # for invalid HTML
  HTMLProofer.check_directory(
    "./_site",
    url_ignore: [/linkedin.com|php-fig.org|bower.io|bost.ocks.org|elementary.io/,/localhost/],
    empty_alt_ignore: true,
    disable_external: false,
    file_ignore: [/\/assets\/reveal\//],
    check_favicon: true
  ).run
  puts "Jekyll successfully built"
end
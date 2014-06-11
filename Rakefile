require 'rubygems'
require 'rake'
require 'net/http'
require 'net/https'
require 'openssl'

task :run_build, [:project] do |t, args|
  abort('No project specified') unless args.has_key? :project
  http = Net::HTTP.new("circleci.com", 443)
  http.use_ssl = true
  http.verify_mode = OpenSSL::SSL::VERIFY_PEER
  
  path = "/api/v1/project/#{ENV['CIRCLE_USER']}/#{args[:project]}/tree/master?circle-token=#{ENV['CIRCLE_TOKEN']}"
  request = Net::HTTP::Post.new(path, {})
  resp = http.request(request)
  puts resp.code
end

